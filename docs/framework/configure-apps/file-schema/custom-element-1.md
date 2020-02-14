---
title: Vlastní element pro SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: 1d0431085a04d3fb817dfe0883779acc4d693084
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214793"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="4fb8f-102">Vlastní element pro SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="4fb8f-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="4fb8f-103">Definuje nastavení v oddílu vlastní konfigurace, která je definována \<sekcí > element a používá třídu <xref:System.Configuration.SingleTagSectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="4fb8f-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="4fb8f-104">[**konfigurační >\<** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="4fb8f-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="4fb8f-105">&nbsp;&nbsp; *\<sectiongroup >*</span><span class="sxs-lookup"><span data-stu-id="4fb8f-105">&nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="4fb8f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fb8f-106">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="4fb8f-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="4fb8f-107">Attributes</span></span>

<span data-ttu-id="4fb8f-108">Atributy a hodnoty atributů jsou definované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="4fb8f-108">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="4fb8f-109">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="4fb8f-109">Parent element</span></span>

|     | <span data-ttu-id="4fb8f-110">Popis</span><span class="sxs-lookup"><span data-stu-id="4fb8f-110">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="4fb8f-111">**Konfigurace \<>** </span><span class="sxs-lookup"><span data-stu-id="4fb8f-111">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="4fb8f-112">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4fb8f-112">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="4fb8f-113">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="4fb8f-113">Child elements</span></span>

<span data-ttu-id="4fb8f-114">Žádná</span><span class="sxs-lookup"><span data-stu-id="4fb8f-114">None</span></span>

## <a name="remarks"></a><span data-ttu-id="4fb8f-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4fb8f-115">Remarks</span></span>

<span data-ttu-id="4fb8f-116">Element **\<>** je vlastní element definovaný [ **\<oddílem >** ](section-element.md) značky v\<m prvku [ **> configSections**](configsections-element-for-configuration.md) .</span><span class="sxs-lookup"><span data-stu-id="4fb8f-116">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="4fb8f-117">Konfigurační systém vrátí objekt <xref:System.Collections.IDictionary> při volání <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4fb8f-117">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="4fb8f-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="4fb8f-118">Example</span></span>

<span data-ttu-id="4fb8f-119">Následující příklad deklaruje vlastní element s názvem **\<sampleSection >** obsahující nastavení přečtená třídou <xref:System.Configuration.SingleTagSectionHandler>:</span><span class="sxs-lookup"><span data-stu-id="4fb8f-119">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="4fb8f-120">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="4fb8f-120">Configuration file</span></span>

<span data-ttu-id="4fb8f-121">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="4fb8f-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="4fb8f-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="4fb8f-122">See also</span></span>

- [<span data-ttu-id="4fb8f-123">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4fb8f-123">Configuration file schema for the .NET Framework</span></span>](index.md)
