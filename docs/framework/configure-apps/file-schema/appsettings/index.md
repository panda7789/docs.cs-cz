---
title: Schéma nastavení aplikace
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 9bf2568c8c18f8f6d18c445e802cc72df18fb8c4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50191140"
---
# <a name="app-settings-schema"></a>Schéma nastavení aplikace

Obsahuje vlastní nastavení aplikace, jako je například cesty k souborům, adresy URL XML webových služeb nebo nějakých jiných informací vlastní konfigurace pro aplikaci.

[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<Přidat >**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<Vymazat >**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<Odebrat >**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)

| Prvek | Popis |
| ------- | ----------- |
| [**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | Obsahuje  **\<Přidat >**,  **\<vymazat >**, a  **\<odebrat >** značek k nastavení aplikace. Má volitelnou **souboru** atribut. |
| [**\<Přidat >**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | Definuje nastavení. Podřízený  **\<appSettings >**. Vyžaduje **klíč** a **hodnotu** atributy. |
| [**\<Vymazat >**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | Vymaže všechna nastavení. Podřízený  **\<appSettings >**. nemá žádné atributy. |
| [**\<Odebrat >**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | Odebere nastavení. Podřízený  **\<appSettings >**. Vyžaduje **klíč** atribut. |

## <a name="appsettings-element"></a>\<appSettings > – element

Tento prvek obsahuje  **\<Přidat >**,  **\<vymazat >**, a  **\<odebrat >** značek k nastavení aplikace. Definuje volitelný atribut pro **souboru**.

## <a name="add-element"></a>\<Přidat > – element

Přidá vlastní nastavení aplikace jako dvojice název/hodnota do kolekce nastavení aplikace. Definuje atributy pro **klíč** a **hodnota**.

## <a name="clear-element"></a>\<Vymazat > – element

Odebere všechny odkazy na zděděná nastavení vlastní aplikace a povoluje pouze odkazy, které jsou přidány pomocí  **\<Přidat >** prvky, které následují  **\<vymazat >** element. Definuje žádné atributy.

## <a name="remove-element"></a>\<Odebrat > – element

Odebere odkaz na nastavení zděděné vlastní aplikace z aplikace nastavení kolekce. Definuje atribut pro **klíč**.

## <a name="example"></a>Příklad

Následující příklad ukazuje soubor nastavení externí aplikace (*custom.config*), který definuje vlastní nastavení aplikace:

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

## <a name="see-also"></a>Viz také:

- [Přehled nastavení aplikace](~/docs/framework/winforms/advanced/application-settings-overview.md)   
- [Architektura nastavení aplikace](~/docs/framework/winforms/advanced/application-settings-architecture.md)
