---
title: <configSections> – element pro element <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: guardrex
ms.author: mairaw
ms.openlocfilehash: dc2bb949c7db4f70c20c3c0b687cacafed8696df
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266765"
---
# <a name="configsections-element-for-configuration"></a>\<configSections > – element pro \<configuration >

Obsahuje konfigurační oddíl a deklarace oboru názvů.

[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<configSections>**

## <a name="attributes"></a>Atributy

Žádná

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |

## <a name="child-elements"></a>Podřízené prvky

|     | Popis |
| --- | ----------- |
| [**\<část >**](~/docs/framework/configure-apps/file-schema/section-element.md) | Obsahuje deklarace oddíl konfigurace. |
| [**\<sectionGroup>**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | Definuje obor názvů pro oddíly konfigurace. |
| [**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | Odstraní předdefinované oddílu nebo skupiny oddílů. |
| [**\<Vymazat >**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | Vymaže všechny dříve definované oddíly a skupin oddílů. |

## <a name="remarks"></a>Poznámky

Pokud tento prvek je v konfiguračním souboru, musí být první podřízený element  **\<konfigurace >** elementu.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak definovat konfiguračního oddílu a určit nastavení pro daný oddíl:

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

Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresáře aplikace.

## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
