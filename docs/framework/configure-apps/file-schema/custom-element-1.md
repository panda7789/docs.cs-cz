---
title: Vlastní element pro SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ac2d01121e81b545556fb082fa7b82c31cccf9da
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118839"
---
# <a name="custom-element-for-singletagsectionhandler"></a>Vlastní element pro SingleTagSectionHandler

Definuje nastavení v oddílu vlastní konfigurace, která je definována \<sekcí > element a používá třídu <xref:System.Configuration.SingleTagSectionHandler>.

[**konfigurační >\<** ](configuration-element.md)   
&nbsp;&nbsp; *\<sectionName>*

## <a name="syntax"></a>Syntaxe

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a>Atributy

Atributy a hodnoty atributů jsou definované uživatelem.

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [**Konfigurace \<>** ](configuration-element.md) | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |

## <a name="child-elements"></a>Podřízené prvky

Žádné

## <a name="remarks"></a>Poznámky

Element **\<>** je vlastní element definovaný [ **\<oddílem >** ](section-element.md) značky v\<m prvku [ **> configSections**](configsections-element-for-configuration.md) . Konfigurační systém vrátí objekt <xref:System.Collections.IDictionary> při volání <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.

## <a name="example"></a>Příklad

Následující příklad deklaruje vlastní element s názvem **\<sampleSection >** obsahující nastavení přečtená třídou <xref:System.Configuration.SingleTagSectionHandler>:

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
