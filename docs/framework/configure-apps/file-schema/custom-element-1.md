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
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="f6b57-102">Vlastní element pro SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="f6b57-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="f6b57-103">Definuje nastavení ve vlastní konfigurační sekci, která je definována \<section> elementem a používá <xref:System.Configuration.SingleTagSectionHandler> třídu.</span><span class="sxs-lookup"><span data-stu-id="f6b57-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="f6b57-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span><span class="sxs-lookup"><span data-stu-id="f6b57-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="f6b57-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6b57-105">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a><span data-ttu-id="f6b57-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="f6b57-106">Attributes</span></span>

<span data-ttu-id="f6b57-107">Atributy a hodnoty atributů jsou definované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="f6b57-107">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="f6b57-108">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="f6b57-108">Parent element</span></span>

|     | <span data-ttu-id="f6b57-109">Description</span><span class="sxs-lookup"><span data-stu-id="f6b57-109">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="f6b57-110">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f6b57-110">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="f6b57-111">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="f6b57-111">Child elements</span></span>

<span data-ttu-id="f6b57-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="f6b57-112">None</span></span>

## <a name="remarks"></a><span data-ttu-id="f6b57-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f6b57-113">Remarks</span></span>

<span data-ttu-id="f6b57-114">**\<sectionName>** Element je vlastní element definovaný [**\<section>**](section-element.md) tagem v [**\<configSections>**](configsections-element-for-configuration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f6b57-114">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="f6b57-115">Konfigurační systém vrátí <xref:System.Collections.IDictionary> objekt při volání <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f6b57-115">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="f6b57-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6b57-116">Example</span></span>

<span data-ttu-id="f6b57-117">Následující příklad deklaruje vlastní element **\<sampleSection>** s názvem, který obsahuje nastavení přečtená <xref:System.Configuration.SingleTagSectionHandler> třídou:</span><span class="sxs-lookup"><span data-stu-id="f6b57-117">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="f6b57-118">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="f6b57-118">Configuration file</span></span>

<span data-ttu-id="f6b57-119">Tento element lze použít v konfiguračním souboru aplikace, v konfiguračním souboru počítače (*Machine. config*) a v souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="f6b57-119">This element can be used in the application configuration file, the machine configuration file (*Machine.config*), and *Web.config* files that aren't at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="f6b57-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6b57-120">See also</span></span>

- [<span data-ttu-id="f6b57-121">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f6b57-121">Configuration file schema for the .NET Framework</span></span>](index.md)
