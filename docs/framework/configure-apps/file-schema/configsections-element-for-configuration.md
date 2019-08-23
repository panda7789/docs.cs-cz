---
title: <configSections> – element pro <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 31b53837e24029fc7ff0b576d95c0213041a434e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927674"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="c334d-102">\<element configSections > pro \<konfigurační ></span><span class="sxs-lookup"><span data-stu-id="c334d-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="c334d-103">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c334d-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="c334d-104">[ **\<> Konfigurace**](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="c334d-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="c334d-105">&nbsp;&nbsp; **\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="c334d-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="c334d-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="c334d-106">Attributes</span></span>

<span data-ttu-id="c334d-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="c334d-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="c334d-108">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="c334d-108">Parent element</span></span>

|     | <span data-ttu-id="c334d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c334d-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c334d-110"> **\<> Konfigurace**</span><span class="sxs-lookup"><span data-stu-id="c334d-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="c334d-111">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c334d-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="c334d-112">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="c334d-112">Child elements</span></span>

|     | <span data-ttu-id="c334d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="c334d-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c334d-114"> **\<> oddílu**</span><span class="sxs-lookup"><span data-stu-id="c334d-114">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="c334d-115">Obsahuje deklaraci konfiguračního oddílu.</span><span class="sxs-lookup"><span data-stu-id="c334d-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="c334d-116"> **\<sectionGroup>** </span><span class="sxs-lookup"><span data-stu-id="c334d-116">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="c334d-117">Definuje obor názvů pro konfigurační oddíly.</span><span class="sxs-lookup"><span data-stu-id="c334d-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="c334d-118"> **\<remove>** </span><span class="sxs-lookup"><span data-stu-id="c334d-118">**\<remove>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="c334d-119">Odebere předdefinovanou sekci nebo skupinu oddílů.</span><span class="sxs-lookup"><span data-stu-id="c334d-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="c334d-120"> **\<Vymazat >** </span><span class="sxs-lookup"><span data-stu-id="c334d-120">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="c334d-121">Vymaže všechny dříve definované oddíly a skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="c334d-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="c334d-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c334d-122">Remarks</span></span>

<span data-ttu-id="c334d-123">Pokud je tento prvek v konfiguračním souboru, musí být prvním podřízeným prvkem  **\<> elementu konfigurace** .</span><span class="sxs-lookup"><span data-stu-id="c334d-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="c334d-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="c334d-124">Example</span></span>

<span data-ttu-id="c334d-125">Následující příklad ukazuje, jak definovat konfigurační oddíl a definovat nastavení pro tuto část:</span><span class="sxs-lookup"><span data-stu-id="c334d-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="c334d-126">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="c334d-126">Configuration file</span></span>

<span data-ttu-id="c334d-127">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="c334d-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="c334d-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c334d-128">See also</span></span>

- [<span data-ttu-id="c334d-129">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c334d-129">Configuration file schema for the .NET Framework</span></span>](index.md)
