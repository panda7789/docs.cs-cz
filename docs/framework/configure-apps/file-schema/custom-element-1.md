---
title: Vlastní prvek pro SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: 0d765a9789ad566428b1fbda6c0863b10b98c363
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345066"
---
# <a name="custom-element-for-singletagsectionhandler"></a>Vlastní prvek pro SingleTagSectionHandler

Definuje nastavení ve vlastním konfiguračním \<oddílu, který <xref:System.Configuration.SingleTagSectionHandler> je definován oddílem> elementa a používá třídu.

konfigurace &nbsp; &nbsp;>[** \<**](configuration-element.md) * \<sekceNázev>*

## <a name="syntax"></a>Syntaxe

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a>Atributy

Atributy a hodnoty atributů jsou definovány uživatelem.

## <a name="parent-element"></a>Nadřazený prvek

|     | Popis |
| --- | ----------- |
| [**\<>konfigurace**](configuration-element.md) | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |

## <a name="child-elements"></a>Podřízené prvky

Žádný

## <a name="remarks"></a>Poznámky

Element ** \<sectionName>** je vlastní prvek definovaný značkou [** \<section>**](section-element.md) v [** \<elementu configSections>.**](configsections-element-for-configuration.md) Konfigurační <xref:System.Collections.IDictionary> systém vrátí <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>objekt při volání .

## <a name="example"></a>Příklad

Následující příklad deklaruje vlastní prvek s názvem <xref:System.Configuration.SingleTagSectionHandler> ** \<sampleSection>,** který obsahuje nastavení přečtené třídou:

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
