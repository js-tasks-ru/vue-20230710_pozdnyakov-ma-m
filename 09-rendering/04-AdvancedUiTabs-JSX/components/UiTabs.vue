<script lang="jsx">
// Предлагается решать задачу с использованием JSX, но вы можете использовать и чистые рендер-функции

import UiTab from './UiTab.vue';

export default {
  name: 'UiTabs',

  props: {
    active: String,
  },

  emits: ['update:active'],

  methods: {
    setActive(tabId) {
      this.$emit('update:active', tabId);
    },
  },

  render() {
    // Получаем переданные вкладки из слота по умолчанию - массив из vnode
    const content = this.$slots.default();
    // Фильтруем узлы по type, оставляя только UiTab
    const tabs = content.filter((item) => item.type === UiTab);
    // Находим активную вкладку, проверяя значение name входных параметров
    const activeTab = tabs.find((tab) => tab.props.name === this.active);

    // Рендерим вкладки:
    // - Ссылки - по параметрам переданных UiTabs
    // - Контент - непосредственно активную вкладку
    return (
      <div class="tabs">
        <div class="tabs__nav" role="tablist">
          {tabs.map((tab) => (
            <a
              class={['tabs__tab', tab.props.name === this.active ? 'tabs__tab_active' : '']}
              role="tab"
              onClick={() => this.setActive(tab.props.name)}
            >
              {tab.props.title}
            </a>
          ))}
        </div>
        <div class="tabs__content">{activeTab}</div>
      </div>
    );
  },
};
</script>

<style scoped>
/* _tabs.css */
.tabs {
  margin: 0;
}

.tabs__content {
}

.tabs__nav {
  display: flex;
  flex-direction: row;
  position: relative;
}

.tabs__nav:before {
  content: '';
  position: absolute;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 2px;
  background-color: var(--grey-2);
}

.tabs__tab {
  display: inline-flex;
  padding: 10px 0;
  font-weight: 400;
  font-size: 18px;
  text-decoration: none;
  line-height: 28px;
  color: var(--grey-8);
  border-bottom: 2px solid transparent;
  cursor: pointer;
  margin-right: 18px;
  transition-duration: 0.2s;
  transition-property: border-color, color;
  box-shadow: none;
  background-color: transparent;
  outline: none;
  position: relative;
  z-index: 1;
}

.tabs__tab:hover,
.tabs__tab.tabs__tab_active {
  border-bottom-color: var(--blue);
  color: var(--blue);
}
</style>
