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
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="3c5e8-102">Vlastní element pro SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="3c5e8-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="3c5e8-103">Definuje nastavení v oddílu vlastní konfigurace, která je definována \<sekcí > element a používá třídu <xref:System.Configuration.SingleTagSectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="3c5e8-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="3c5e8-104">[**konfigurační >\<** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="3c5e8-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="3c5e8-105">&nbsp;&nbsp; *\<sectionName>*</span><span class="sxs-lookup"><span data-stu-id="3c5e8-105">&nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="3c5e8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c5e8-106">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="3c5e8-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="3c5e8-107">Attributes</span></span>

<span data-ttu-id="3c5e8-108">Atributy a hodnoty atributů jsou definované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="3c5e8-108">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="3c5e8-109">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="3c5e8-109">Parent element</span></span>

|     | <span data-ttu-id="3c5e8-110">Popis</span><span class="sxs-lookup"><span data-stu-id="3c5e8-110">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3c5e8-111">**Konfigurace \<>** </span><span class="sxs-lookup"><span data-stu-id="3c5e8-111">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="3c5e8-112">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3c5e8-112">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="3c5e8-113">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="3c5e8-113">Child elements</span></span>

<span data-ttu-id="3c5e8-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="3c5e8-114">None</span></span>

## <a name="remarks"></a><span data-ttu-id="3c5e8-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3c5e8-115">Remarks</span></span>

<span data-ttu-id="3c5e8-116">Element **\<>** je vlastní element definovaný [ **\<oddílem >** ](section-element.md) značky v\<m prvku [ **> configSections**](configsections-element-for-configuration.md) .</span><span class="sxs-lookup"><span data-stu-id="3c5e8-116">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="3c5e8-117">Konfigurační systém vrátí objekt <xref:System.Collections.IDictionary> při volání <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3c5e8-117">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="3c5e8-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="3c5e8-118">Example</span></span>

<span data-ttu-id="3c5e8-119">Následující příklad deklaruje vlastní element s názvem **\<sampleSection >** obsahující nastavení přečtená třídou <xref:System.Configuration.SingleTagSectionHandler>:</span><span class="sxs-lookup"><span data-stu-id="3c5e8-119">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="3c5e8-120">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="3c5e8-120">Configuration file</span></span>

<span data-ttu-id="3c5e8-121">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="3c5e8-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c5e8-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c5e8-122">See also</span></span>

- [<span data-ttu-id="3c5e8-123">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3c5e8-123">Configuration file schema for the .NET Framework</span></span>](index.md)
