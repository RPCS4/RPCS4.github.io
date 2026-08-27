<script setup lang="ts">
import 'vfonts/FiraSans.css';

import { GlobalThemeOverrides, darkTheme, NLayout } from 'naive-ui';
import { CardThemeVars } from 'naive-ui/es/card/styles';
import { TypographyThemeVars } from 'naive-ui/es/typography/styles';
import { GradientTextThemeVars } from 'naive-ui/es/gradient-text/styles';
import { MenuThemeVars } from 'naive-ui/es/menu/styles';
import { ButtonThemeVars } from 'naive-ui/es/button/styles';

const menuOverrides: Partial<MenuThemeVars> = {
  fontSize: '12pt',
  itemTextColorActiveHorizontal: '#4C3E9C',
  itemIconColorActiveHorizontal: '#4C3E9C',
};

const darkMenu: Partial<MenuThemeVars> = {
  ...menuOverrides,
  itemTextColorHorizontal: '#F8F2F1',
  groupTextColor: '#F8F2F1',
  itemTextColorHoverHorizontal: '#739AF0',
  itemIconColorHoverHorizontal: '#739AF0',
};

const gradientTextOverrides: Partial<GradientTextThemeVars> = {
  rotate: '188deg',
  colorEndInfo: '#3633fa',
  colorStartInfo: '#9600ff',
};

const typographyOverrides: Partial<TypographyThemeVars> = {
  headerFontSize1: '30pt',
  headerFontWeight: 'bold',
  headerFontSize2: '18pt',
  headerFontSize3: '14pt',
  headerMargin3: '0px',
};

const darkTypography: Partial<TypographyThemeVars> = {
  ...typographyOverrides,
  textColor: '#F8F2F1'
};

const cardOverrides: Partial<CardThemeVars> = {
  titleFontWeight: 'bold',
  titleFontSizeHuge: '16pt',
  titleFontSizeMedium: '16pt',
  titleFontSizeSmall: '16pt',
  fontSizeMedium: '12pt',
  borderRadius: '20px'
};

const buttonOverrides: Partial<ButtonThemeVars> = {
  textColorHover: '#3633fa',
  borderHover: '1px solid #3633fa',
  textColorFocus: '#a2a1ff',
  borderFocus: '1px solid #a2a1ff'
};

const darkThemeOverrides: GlobalThemeOverrides = {
  common: {
    baseColor: '#121420',
    primaryColor: '#F8F2F1',
    cardColor: '#121420',
  },
  Typography: darkTypography,
  Card: cardOverrides,
  GradientText: gradientTextOverrides,
  Menu: darkMenu,
  Button: buttonOverrides,
};
</script>

<template>
  <n-config-provider
    :theme="darkTheme"
    :theme-overrides="darkThemeOverrides"
  >
    <n-layout>
      <div class="wrapper">
        <div class="top-portion-wrapper">
          <Suspense>
            <TopBarMenu />
          </Suspense>

          <div class="columns">
            <div
              id="main-column"
              class="column"
            >
              <div class="top-main">
                <Suspense>
                  <Hook />
                </Suspense>
              </div>

              <div class="column-content" />
            </div>

            <div
              id="right-column"
              class="column"
            >
              <div class="top-right">
                <MainCard />
              </div>

              <div class="column-content">
                <!-- <iframe src="https://discord.com/widget?id=1454877158064390196&theme=dark" width="250" height="400" allowtransparency="true" frameborder="0" sandbox="allow-popups allow-popups-to-escape-sandbox allow-same-origin allow-scripts"></iframe> -->
              </div>
            </div>
          </div>
        </div>

        <n-divider />

        <div class="bottom-portion-wrapper">
          <n-divider />

          <n-text class="copyright-text">
            © {{ new Date().getFullYear() }} - RPCS4
          </n-text>
        </div>
      </div>
    </n-layout>
  </n-config-provider>
</template>

<style scoped>
.n-layout {
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
}

.n-divider {
  margin: 0px 16px;
}

.copyright-text {
  display: flex;
  align-self: flex-start;
  padding-left: 10%;
  font-weight: bold;
  font-size: 12pt;
}

.layout-dark {
  background-image: url('/assets/background-dark.png');
}

.wrapper {
  height: 100%;
  overflow: hidden;
  margin: 10px 10px;
  box-sizing: border-box;
}

.top-portion-wrapper {
  display: flex;
  flex-direction: column;
}

.bottom-portion-wrapper {
  margin-top: 30px;
  gap: 16px;
  display: flex;
  flex-flow: column nowrap;
  align-items: center;
}

.columns {
  display: flex;
  flex-flow: row wrap;
  justify-content: center;
  align-items: stretch;
  margin-top: 20px;
}

.column {
  height: 100%;
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  margin: 8px;
}

.column-content {
  display: flex;
  flex-flow: column nowrap;
  align-items: center;
  gap: 16px;
}

#main-column {
  flex-shrink: 1;
  flex-grow: 2;
  align-self: center;
  align-items: center;
  gap: 20px;
}

#right-column {
  flex-grow: 1;
  gap: 16px;
  padding-right: 10px;
  align-self: center;
  align-items: center;
}

.right-pane-button {
  margin: 15px;
  padding: 16px;
}

.top-main {
  flex-shrink: 0;
}

.top-right {
  flex-shrink: 0;
  display: flex;
  padding-top: 15%;
}
</style>
