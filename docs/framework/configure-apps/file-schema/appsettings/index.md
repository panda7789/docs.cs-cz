---
title: Schéma nastavení aplikace
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: d02f9f952c0ca7651d27571111a2d29f3d1130fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921292"
---
# <a name="app-settings-schema"></a>Schéma nastavení aplikace

Obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci pro aplikaci.

[ **\<> Konfigurace**](../configuration-element.md)   
&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<add>** ](add-element-for-appsettings.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Vymazat >** ](clear-element-for-appsettings.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<odebrat >** ](remove-element-for-appsettings.md)

| Prvek | Popis |
| ------- | ----------- |
| [ **\<appSettings>** ](appsettings-element-for-configuration.md) | **Obsahuje\<> Přidat**,  **\<vymazat >** a  **\<odebrat značky >** pro řízení nastavení aplikace. Má volitelný atribut **souboru** . |
| [ **\<add>** ](add-element-for-appsettings.md) | Definuje nastavení. Podřízený objekt appSettings >.  **\<** Vyžaduje atributy **klíče** a **hodnoty** . |
| [ **\<Vymazat >** ](clear-element-for-appsettings.md) | Vymaže všechna nastavení. Podřízený objekt appSettings >.  **\<** Nemá žádné atributy. |
| [ **\<remove>** ](remove-element-for-appsettings.md) | Odebere nastavení. Podřízený objekt appSettings >.  **\<** Vyžaduje atribut **Key** . |

## <a name="appsettings-element"></a>\<appSettings – element > element

Tento prvek obsahuje  **\<přidání >** ,  **\<vymazání >** a  **\<odebrání značek >** pro řízení nastavení aplikace. Definuje volitelný atribut pro **soubor**.

## <a name="add-element"></a>\<Přidat > element

Přidá vlastní nastavení aplikace jako dvojici název-hodnota do kolekce nastavení aplikace. Definuje atributy pro **klíč** a **hodnotu**.

## <a name="clear-element"></a>\<Vymazat > element

Odebere všechny odkazy na zděděná nastavení vlastní aplikace a povoluje pouze odkazy, které jsou přidány  **\<přidáním >** prvků po  **\<elementu Clear >** . Nedefinuje žádné atributy.

## <a name="remove-element"></a>\<Odebrat element >

Odebere odkaz na zděděné nastavení vlastní aplikace z kolekce nastavení aplikace. Definuje atribut pro **klíč**.

## <a name="example"></a>Příklad

Následující příklad ukazuje soubor nastavení externí aplikace (*Custom. config*), který definuje vlastní nastavení aplikace:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

Následující příklad ukazuje konfigurační soubor aplikace, který využívá nastavení v souboru externího nastavení a nastavuje vlastní nastavení aplikace:

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a>Viz také:

- [Přehled nastavení aplikace](../../../winforms/advanced/application-settings-overview.md)
- [Architektura nastavení aplikace](../../../winforms/advanced/application-settings-architecture.md)
