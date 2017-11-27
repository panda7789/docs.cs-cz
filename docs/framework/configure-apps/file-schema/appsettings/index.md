---
title: "Schéma nastavení aplikace"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1d51d06895e61be60bbe9153eacb2028cb32a1fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="app-settings-schema"></a>Schéma nastavení aplikace

Obsahuje nastavení vlastní aplikace, například cesty k souborům, adresy URL XML webových služeb nebo všechny ostatní informace vlastní konfigurace pro aplikaci.

[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<Přidat >**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<Clear >**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<Odebrat >**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)

| Prvek | Popis |
| ------- | ----------- |
| [**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | Obsahuje  **\<Přidat >**,  **\<clear >**, a  **\<odebrat >** značky pro řízení nastavení aplikace. Má volitelný **souboru** atribut. |
| [**\<Přidat >**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | Definuje nastavení. Podřízená položka  **\<appSettings >**. Vyžaduje **klíč** a **hodnotu** atributy. |
| [**\<Clear >**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | Vymaže všechna nastavení. Podřízená položka  **\<appSettings >**. Nemá žádné atributy. |
| [**\<Odebrat >**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | Odebere nastavení. Podřízená položka  **\<appSettings >**. Vyžaduje **klíč** atribut. |

## <a name="appsettings-element"></a>\<appSettings > elementu

Tento prvek obsahuje  **\<Přidat >**,  **\<clear >**, a  **\<odebrat >** značky pro řízení nastavení aplikace. Definuje volitelný atribut pro **soubor**.

## <a name="add-element"></a>\<Přidat > elementu

Přidá vlastní nastavení aplikace jako dvojici název/hodnota do kolekce nastavení aplikace. Definuje atributy pro **klíč** a **hodnotu**.

## <a name="clear-element"></a>\<Clear > elementu

Odebere všechny odkazy na zděděná vlastní nastavení aplikace a umožňuje pouze odkazy, které přidá  **\<Přidat >** následující prvky  **\<clear >** element. Definuje žádné atributy.

## <a name="remove-element"></a>\<Odebrat > elementu

Odebere odkaz na zděděné vlastní nastavení aplikace z kolekce nastavení aplikace. Definuje atribut pro **klíč**.

## <a name="example"></a>Příklad

Následující příklad ukazuje soubor s nastavením externí aplikaci (*custom.config*), který definuje vlastní nastavení aplikace:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

Následující příklad ukazuje konfigurační soubor aplikace, která načítá nastavení v souboru externích nastavení a nastaví vlastní nastavení aplikace:

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a>Viz také

[Přehled nastavení aplikace](~/docs/framework/winforms/advanced/application-settings-overview.md)   
[Architektura nastavení aplikace](~/docs/framework/winforms/advanced/application-settings-architecture.md)
