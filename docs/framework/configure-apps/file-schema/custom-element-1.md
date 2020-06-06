---
title: Vlastní element pro SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: a40f35838655f6021af0b2e966335803ec8c16b4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "80635403"
---
# <a name="custom-element-for-singletagsectionhandler"></a>Vlastní element pro SingleTagSectionHandler

Definuje nastavení ve vlastní konfigurační sekci, která je definována \<section> elementem a používá <xref:System.Configuration.SingleTagSectionHandler> třídu.

[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*

## <a name="syntax"></a>Syntaxe

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a>Atributy

Atributy a hodnoty atributů jsou definované uživatelem.

## <a name="parent-element"></a>Nadřazený element

|     | Description |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |

## <a name="child-elements"></a>Podřízené prvky

Žádné

## <a name="remarks"></a>Poznámky

**\<sectionName>** Element je vlastní element definovaný [**\<section>**](section-element.md) tagem v [**\<configSections>**](configsections-element-for-configuration.md) elementu. Konfigurační systém vrátí <xref:System.Collections.IDictionary> objekt při volání <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType> .

## <a name="example"></a>Příklad

Následující příklad deklaruje vlastní element **\<sampleSection>** s názvem, který obsahuje nastavení přečtená <xref:System.Configuration.SingleTagSectionHandler> třídou:

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

Tento element lze použít v konfiguračním souboru aplikace, v konfiguračním souboru počítače (*Machine. config*) a v souborech *Web. config* , které nejsou na úrovni adresáře aplikace.

## <a name="see-also"></a>Viz také

- [Schéma konfiguračního souboru pro .NET Framework](index.md)
