---
title: Schéma nastavení aplikace
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
ms.openlocfilehash: 0a3363b35a6fc8bd27753eb034f8a1e95feb5292
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215432"
---
# <a name="app-settings-schema"></a>Schéma nastavení aplikace

Obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci pro aplikaci.

[**konfigurační >\<** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<přidat >** ](add-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clear >** ](clear-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<odebrat >** ](remove-element-for-appsettings.md)

| Prvek | Popis |
| ------- | ----------- |
| [ **\<appSettings >** ](appsettings-element-for-configuration.md) | Obsahuje **\<přidat >** , **\<vymazat >** a **\<odebrat značky >** pro řízení nastavení aplikace. Má volitelný atribut **souboru** . |
| [ **\<přidat >** ](add-element-for-appsettings.md) | Definuje nastavení. Podřízená položka **>\<appSettings** Vyžaduje atributy **klíče** a **hodnoty** . |
| [ **\<vymazat >** ](clear-element-for-appsettings.md) | Vymaže všechna nastavení. Podřízená položka **>\<appSettings** Nemá žádné atributy. |
| [ **\<odebrat >** ](remove-element-for-appsettings.md) | Odebere nastavení. Podřízená položka **>\<appSettings** Vyžaduje atribut **Key** . |

## <a name="appsettings-element"></a>element \<appSettings >

Tento prvek obsahuje **\<přidat >** , **\<vymazat >** a **\<odebrat značky >** pro řízení nastavení aplikace. Definuje volitelný atribut pro **soubor**.

## <a name="add-element"></a>\<přidat > element

Přidá vlastní nastavení aplikace jako dvojici název-hodnota do kolekce nastavení aplikace. Definuje atributy pro **klíč** a **hodnotu**.

## <a name="clear-element"></a>\<vymazat > element

Odebere všechny odkazy na zděděná vlastní nastavení aplikace a povoluje pouze odkazy, které jsou přidány pomocí **\<přidat >** prvky za **\<jasný >** element. Nedefinuje žádné atributy.

## <a name="remove-element"></a>\<odebrat element >

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

## <a name="see-also"></a>Viz také

- [Přehled nastavení aplikace](../../../winforms/advanced/application-settings-overview.md)
- [Architektura nastavení aplikace](../../../winforms/advanced/application-settings-architecture.md)
