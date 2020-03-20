---
title: <configSections> – element pro <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 55116f1fe6fdffffea8f26d8a4de783c7305ada3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155346"
---
# <a name="configsections-element-for-configuration"></a>\<configSections> \<element pro konfiguraci>

Obsahuje konfigurační oddíl a deklarace oboru názvů.

konfigurace &nbsp; &nbsp;>[** \<**](configuration-element.md) **konfiguračnísekce \<>**

## <a name="attributes"></a>Atributy

Žádný

## <a name="parent-element"></a>Nadřazený prvek

|     | Popis |
| --- | ----------- |
| [**\<>konfigurace**](configuration-element.md) | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |

## <a name="child-elements"></a>Podřízené prvky

|     | Popis |
| --- | ----------- |
| [**\<>oddílu**](section-element.md) | Obsahuje deklaraci oddílu konfigurace. |
| [**\<oddílSkupina>**](sectiongroup-element-for-configsections.md) | Definuje obor názvů pro oddíly konfigurace. |
| [**\<odebrat>**](remove-element-for-configsections.md) | Odebere předdefinovaný oddíl nebo skupinu oddílů. |
| [**\<jasné>**](clear-element-for-configsections.md) | Vymaže všechny dříve definované oddíly a skupiny oddílů. |

## <a name="remarks"></a>Poznámky

Pokud je tento prvek v konfiguračním souboru, musí se jednat o první podřízený prvek ** \<prvku konfigurace>.**

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak definovat konfigurační oddíl a definovat nastavení pro tento oddíl:

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>Konfigurační soubor

Tento prvek lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače *(Machine.config*) a souborech *Web.config,* které nejsou na úrovni adresáře aplikace.

## <a name="see-also"></a>Viz také

- [Schéma konfiguračního souboru pro rozhraní .NET Framework](index.md)
