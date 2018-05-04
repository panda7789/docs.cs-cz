---
title: '&lt;configSections&gt; element pro &lt;konfigurace&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 33406a67389cdf857fa5030e20d8a4dec7662741
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="configsections-element-for-configuration"></a>\<configSections > elementu pro \<konfigurace >

Obsahuje konfigurační oddíl a deklarace oboru názvů.

[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<configSections >**

## <a name="attributes"></a>Atributy

Žádné

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |

## <a name="child-elements"></a>Podřízené prvky

|     | Popis |
| --- | ----------- |
| [**\<část >**](~/docs/framework/configure-apps/file-schema/section-element.md) | Obsahuje deklaraci konfigurační oddíl. |
| [**\<sectionGroup >**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | Definuje obor názvů pro konfigurační oddíly. |
| [**\<Odebrat >**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | Odstraní předdefinované části nebo skupinu oddílů. |
| [**\<Clear >**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | Vymaže všechny dříve definované oddíly a skupiny oddílů. |

## <a name="remarks"></a>Poznámky

Pokud tento element je v konfiguračním souboru, musí být první podřízený prvek  **\<konfigurace >** element.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak definovat oddíl konfigurace a nastavení pro daný oddíl:

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

Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresář aplikace.

## <a name="see-also"></a>Viz také

[Schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
