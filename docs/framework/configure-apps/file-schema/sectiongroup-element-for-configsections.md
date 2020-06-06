---
title: <sectionGroup> – element pro <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
ms.openlocfilehash: eb221027470fe6e485f8fcc4b939b71e4f219712
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215263"
---
# <a name="sectiongroup-element-for-configsections"></a>\<sectionGroup> – element pro \<configSections>

Definuje obor názvů pro konfigurační oddíly.

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**

## <a name="syntax"></a>Syntaxe

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a>Atribut

|           | Popis |
| --------- | ----------- |
| **Jméno**  | Požadovaný atribut.<br><br>Určuje název skupiny oddílů, kterou definujete. |

## <a name="parent-element"></a>Nadřazený element

|     | Description |
| --- | ----------- |
| [**\<configSections>** Objekt](configsections-element-for-configuration.md) | Obsahuje konfigurační oddíl a deklarace oboru názvů. |

## <a name="child-elements"></a>Podřízené prvky

|     | Description |
| --- | ----------- |
| [**\<section>**](section-element.md) | Obsahuje deklaraci konfiguračního oddílu. |

## <a name="remarks"></a>Poznámky

Deklarace skupiny oddílů vytvoří značku kontejneru pro konfigurační oddíly a zajistí, že nedojde ke konfliktu názvů s konfiguračními oddíly definovanými někým jiným. Prvky lze vnořit **\<sectionGroup>** do sebe navzájem.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak deklarovat skupinu oddílů a deklarovat oddíly v rámci skupiny oddílů:

```xml
<configuration>
  <configSections>
    <sectionGroup name="mySectionGroup">
      <section name="mySection"
               type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a>Konfigurační soubor

Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.

## <a name="see-also"></a>Viz také

- [Schéma konfiguračního souboru pro .NET Framework](index.md)
