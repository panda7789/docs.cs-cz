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
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="ed067-102">Vlastní prvek pro SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="ed067-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="ed067-103">Definuje nastavení ve vlastním konfiguračním \<oddílu, který <xref:System.Configuration.SingleTagSectionHandler> je definován oddílem> elementa a používá třídu.</span><span class="sxs-lookup"><span data-stu-id="ed067-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="ed067-104">konfigurace &nbsp; &nbsp;>[\*\* \<\*\*](configuration-element.md) \* \<sekceNázev>\*</span><span class="sxs-lookup"><span data-stu-id="ed067-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="ed067-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed067-105">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a><span data-ttu-id="ed067-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="ed067-106">Attributes</span></span>

<span data-ttu-id="ed067-107">Atributy a hodnoty atributů jsou definovány uživatelem.</span><span class="sxs-lookup"><span data-stu-id="ed067-107">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="ed067-108">Nadřazený prvek</span><span class="sxs-lookup"><span data-stu-id="ed067-108">Parent element</span></span>

|     | <span data-ttu-id="ed067-109">Popis</span><span class="sxs-lookup"><span data-stu-id="ed067-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ed067-110">**\<>konfigurace**</span><span class="sxs-lookup"><span data-stu-id="ed067-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="ed067-111">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ed067-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="ed067-112">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="ed067-112">Child elements</span></span>

<span data-ttu-id="ed067-113">Žádný</span><span class="sxs-lookup"><span data-stu-id="ed067-113">None</span></span>

## <a name="remarks"></a><span data-ttu-id="ed067-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ed067-114">Remarks</span></span>

<span data-ttu-id="ed067-115">Element \*\* \<sectionName>\*\* je vlastní prvek definovaný značkou [\*\* \<section>\*\*](section-element.md) v [\*\* \<elementu configSections>.\*\*](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="ed067-115">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="ed067-116">Konfigurační <xref:System.Collections.IDictionary> systém vrátí <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>objekt při volání .</span><span class="sxs-lookup"><span data-stu-id="ed067-116">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="ed067-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="ed067-117">Example</span></span>

<span data-ttu-id="ed067-118">Následující příklad deklaruje vlastní prvek s názvem <xref:System.Configuration.SingleTagSectionHandler> \*\* \<sampleSection>,\*\* který obsahuje nastavení přečtené třídou:</span><span class="sxs-lookup"><span data-stu-id="ed067-118">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="ed067-119">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="ed067-119">Configuration file</span></span>

<span data-ttu-id="ed067-120">Tento prvek lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače *(Machine.config*) a souborech *Web.config,* které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="ed067-120">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed067-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed067-121">See also</span></span>

- [<span data-ttu-id="ed067-122">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ed067-122">Configuration file schema for the .NET Framework</span></span>](index.md)
