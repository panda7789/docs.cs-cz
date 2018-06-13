---
title: Vlastní element pro SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 07bc0d9560546f4946d34413697fb0adcf84c58d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743274"
---
# <a name="custom-element-for-singletagsectionhandler"></a>Vlastní element pro SingleTagSectionHandler

Definuje nastavení v části vlastní konfigurace, který je definován <section> element a používá <xref:System.Configuration.SingleTagSectionHandler> třídy.

[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;*\<sectionName>*

## <a name="syntax"></a>Syntaxe

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a>Atributy

Atributy a hodnoty atributů jsou definované uživatelem.

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework. |

## <a name="child-elements"></a>Podřízené prvky

Žádné

## <a name="remarks"></a>Poznámky

**\<SectionName >** element je vlastní definované [  **\<části >** ](~/docs/framework/configure-apps/file-schema/section-element.md) značky v [  **\<configSections >** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) element. Konfigurační systém vrátí <xref:System.Collections.IDictionary> objektu při volání <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.

## <a name="example"></a>Příklad

Následující příklad deklaruje vlastní prvek s názvem  **\<sampleSection >** obsahující nastavení číst <xref:System.Configuration.SingleTagSectionHandler> třídy:

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
