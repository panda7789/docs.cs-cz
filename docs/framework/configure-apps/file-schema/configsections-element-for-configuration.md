---
title: <configSections> – element pro <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 31b53837e24029fc7ff0b576d95c0213041a434e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927674"
---
# <a name="configsections-element-for-configuration"></a>\<element configSections > pro \<konfigurační >

Obsahuje konfigurační oddíl a deklarace oboru názvů.

[ **\<> Konfigurace**](configuration-element.md)   
&nbsp;&nbsp; **\<configSections>**

## <a name="attributes"></a>Atributy

Žádné

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [ **\<> Konfigurace**](configuration-element.md) | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |

## <a name="child-elements"></a>Podřízené prvky

|     | Popis |
| --- | ----------- |
| [ **\<> oddílu**](section-element.md) | Obsahuje deklaraci konfiguračního oddílu. |
| [ **\<sectionGroup>** ](sectiongroup-element-for-configsections.md) | Definuje obor názvů pro konfigurační oddíly. |
| [ **\<remove>** ](remove-element-for-configsections.md) | Odebere předdefinovanou sekci nebo skupinu oddílů. |
| [ **\<Vymazat >** ](clear-element-for-configsections.md) | Vymaže všechny dříve definované oddíly a skupiny oddílů. |

## <a name="remarks"></a>Poznámky

Pokud je tento prvek v konfiguračním souboru, musí být prvním podřízeným prvkem  **\<> elementu konfigurace** .

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak definovat konfigurační oddíl a definovat nastavení pro tuto část:

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

Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.

## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru pro .NET Framework](index.md)
