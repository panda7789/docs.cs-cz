---
title: <configSections> – element pro <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 55116f1fe6fdffffea8f26d8a4de783c7305ada3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155346"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="aac00-102">\<configSections> – element pro \<configuration></span><span class="sxs-lookup"><span data-stu-id="aac00-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="aac00-103">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="aac00-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="aac00-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="aac00-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="aac00-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="aac00-105">Attributes</span></span>

<span data-ttu-id="aac00-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="aac00-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="aac00-107">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="aac00-107">Parent element</span></span>

|     | <span data-ttu-id="aac00-108">Description</span><span class="sxs-lookup"><span data-stu-id="aac00-108">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="aac00-109">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aac00-109">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="aac00-110">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="aac00-110">Child elements</span></span>

|     | <span data-ttu-id="aac00-111">Description</span><span class="sxs-lookup"><span data-stu-id="aac00-111">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="aac00-112">Obsahuje deklaraci konfiguračního oddílu.</span><span class="sxs-lookup"><span data-stu-id="aac00-112">Contains a configuration section declaration.</span></span> |
| [**\<sectionGroup>**](sectiongroup-element-for-configsections.md) | <span data-ttu-id="aac00-113">Definuje obor názvů pro konfigurační oddíly.</span><span class="sxs-lookup"><span data-stu-id="aac00-113">Defines a namespace for configuration sections.</span></span> |
| [**\<remove>**](remove-element-for-configsections.md) | <span data-ttu-id="aac00-114">Odebere předdefinovanou sekci nebo skupinu oddílů.</span><span class="sxs-lookup"><span data-stu-id="aac00-114">Removes a predefined section or section group.</span></span> |
| [**\<clear>**](clear-element-for-configsections.md) | <span data-ttu-id="aac00-115">Vymaže všechny dříve definované oddíly a skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="aac00-115">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="aac00-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aac00-116">Remarks</span></span>

<span data-ttu-id="aac00-117">Pokud je tento prvek v konfiguračním souboru, musí být prvním podřízeným elementem **\<configuration>** elementu.</span><span class="sxs-lookup"><span data-stu-id="aac00-117">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="aac00-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="aac00-118">Example</span></span>

<span data-ttu-id="aac00-119">Následující příklad ukazuje, jak definovat konfigurační oddíl a definovat nastavení pro tuto část:</span><span class="sxs-lookup"><span data-stu-id="aac00-119">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="aac00-120">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="aac00-120">Configuration file</span></span>

<span data-ttu-id="aac00-121">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="aac00-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="aac00-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="aac00-122">See also</span></span>

- [<span data-ttu-id="aac00-123">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="aac00-123">Configuration file schema for the .NET Framework</span></span>](index.md)
