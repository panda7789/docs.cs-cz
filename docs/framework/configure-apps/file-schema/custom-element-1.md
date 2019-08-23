---
title: Vlastní element pro SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 8fae3673fe72d036802cb1a8366aaa2430c38884
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927503"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="7f099-102">Vlastní element pro SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="7f099-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="7f099-103">Definuje nastavení ve vlastní konfigurační sekci, která je definována \<oddílem > elementem a <xref:System.Configuration.SingleTagSectionHandler> používá třídu.</span><span class="sxs-lookup"><span data-stu-id="7f099-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="7f099-104">[ **\<> Konfigurace**](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="7f099-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="7f099-105">&nbsp;&nbsp; *\<sectionName>*</span><span class="sxs-lookup"><span data-stu-id="7f099-105">&nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="7f099-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f099-106">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="7f099-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="7f099-107">Attributes</span></span>

<span data-ttu-id="7f099-108">Atributy a hodnoty atributů jsou definované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="7f099-108">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="7f099-109">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="7f099-109">Parent element</span></span>

|     | <span data-ttu-id="7f099-110">Popis</span><span class="sxs-lookup"><span data-stu-id="7f099-110">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="7f099-111"> **\<> Konfigurace**</span><span class="sxs-lookup"><span data-stu-id="7f099-111">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="7f099-112">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7f099-112">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="7f099-113">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="7f099-113">Child elements</span></span>

<span data-ttu-id="7f099-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="7f099-114">None</span></span>

## <a name="remarks"></a><span data-ttu-id="7f099-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f099-115">Remarks</span></span>

<span data-ttu-id="7f099-116">[ **\<** ](section-element.md) [ **\<** ](configsections-element-for-configuration.md) Element **sectionGroup > je vlastní element definovaný oddílem >m tagu v prvku configSections >. \<**</span><span class="sxs-lookup"><span data-stu-id="7f099-116">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="7f099-117">Konfigurační systém vrátí <xref:System.Collections.IDictionary> objekt při volání <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7f099-117">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="7f099-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="7f099-118">Example</span></span>

<span data-ttu-id="7f099-119">Následující příklad deklaruje vlastní element s názvem  **\<sampleSection >** , který obsahuje <xref:System.Configuration.SingleTagSectionHandler> nastavení čtená třídou:</span><span class="sxs-lookup"><span data-stu-id="7f099-119">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="7f099-120">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="7f099-120">Configuration file</span></span>

<span data-ttu-id="7f099-121">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="7f099-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f099-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f099-122">See also</span></span>

- [<span data-ttu-id="7f099-123">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7f099-123">Configuration file schema for the .NET Framework</span></span>](index.md)
