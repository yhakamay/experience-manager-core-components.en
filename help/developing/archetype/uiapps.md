---
title: ui.apps Module of the AEM Project Archetype
description: ui.apps Module of the AEM Project Archetype
feature: Core Components, AEM Project Archetype
role: Architect, Developer, Admin
exl-id: fc63a19a-3253-44ee-96e2-bb5544c2235b
---
# ui.apps Module of the AEM Project Archetype {#uiapps-module}

The ui.apps maven module (`<src-directory>/<project>/ui.apps`) includes all of the rendering code needed for the site beneath `/apps`. This includes CSS/JS that will be stored in an AEM format called [clientlibs.](uifrontend.md#clientlibs) This also includes HTL scripts for rendering dynamic HTML. You can think of the ui.apps module as a map to the structure in the JCR but in a format that can be stored on a file system and committed to source control.

The Apache Jackrabbit FileVault Package plugin is used to compile the contents of the ui.apps module into an AEM package that can be deployed to AEM. The global configurations for the plugin are defined in the parent pom.xml.

## Parent POM {#parent-pom}

[The parent POM](/help/developing/archetype/using.md#parent-pom) (`<src>/<project>/pom.xml`) includes `<plugin>` sections which define various configurations for the plugins used in the project. This includes a configuration for the `filterSource` for the Jackrabbit FileVault Package Plugin. The `filterSource` points to the location of the `filter.xml` file that is used to define the jcr paths that are included in the package.

In addition to the Jackrabbit FileVault Package Plugin is a definition of the Content Package Plugin which is used to then push the package into AEM. Note that variables for `aem.host`, `aem.port`, `vault.user`, and `vault.password` are used that correspond to the global properties defined in the same parent POM.

## ui.apps/pom.xml {#uiapps-pom}

Notice that core.wcm.components.all and core.wcm.components.examples packages are included as a sub-package. This will deploy the Core Components package along with the WKND code each time.

The core.wcm.components.all and core.wcm.components.examples are included as dependencies in the dependency list. However as a best practice, versions for dependencies are omitted here and managed in the [parent pom file](/help/developing/archetype/using.md#core-components).

## filter.xml {#filter}

The `filter.xml` file for the ui.apps module is found at `<src>/<project>/ui.apps/src/main/content/META-INF/vault/filter.xml` and contains the paths that will be included and installed with the ui.apps package.
