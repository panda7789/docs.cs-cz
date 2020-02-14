---
title: <add> – element pro <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
ms.openlocfilehash: 5c7de79ec626966e71d461dd3865b294a8979db2
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214815"
---
# <a name="add-element-for-appsettings"></a>\<přidat > element pro \<appSettings >

Přidá vlastní nastavení aplikace.

[**konfigurační >\<** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<přidat >**

## <a name="syntax"></a>Syntaxe

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a>Atributy

|           | Popis |
| --------- | ----------- |
| **key**   | Požadovaný atribut.<br><br>Určuje název klíče, který chcete přidat. |
| **value** | Požadovaný atribut.<br><br>Určuje hodnotu klíče, který se má přidat. |

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [ **\<appSettings >** ](appsettings-element-for-configuration.md) | Obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci pro aplikaci. |

## <a name="child-elements"></a>Podřízené prvky

Žádná

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak přidat vlastní nastavení konfigurace pro název aplikace:

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

Následující příklad používá element `<add>` k definování dvou nastavení kompatibility v aplikaci ASP.NET:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a>Viz také

- [Schéma konfiguračního souboru pro .NET Framework](../index.md)
