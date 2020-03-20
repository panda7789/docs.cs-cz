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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155346"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="298e2-102">\<configSections> \<element pro konfiguraci></span><span class="sxs-lookup"><span data-stu-id="298e2-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="298e2-103">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="298e2-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="298e2-104">konfigurace &nbsp; &nbsp;>[\*\* \<\*\*](configuration-element.md) **konfiguračnísekce \<>**</span><span class="sxs-lookup"><span data-stu-id="298e2-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="298e2-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="298e2-105">Attributes</span></span>

<span data-ttu-id="298e2-106">Žádný</span><span class="sxs-lookup"><span data-stu-id="298e2-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="298e2-107">Nadřazený prvek</span><span class="sxs-lookup"><span data-stu-id="298e2-107">Parent element</span></span>

|     | <span data-ttu-id="298e2-108">Popis</span><span class="sxs-lookup"><span data-stu-id="298e2-108">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="298e2-109">**\<>konfigurace**</span><span class="sxs-lookup"><span data-stu-id="298e2-109">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="298e2-110">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="298e2-110">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="298e2-111">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="298e2-111">Child elements</span></span>

|     | <span data-ttu-id="298e2-112">Popis</span><span class="sxs-lookup"><span data-stu-id="298e2-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="298e2-113">**\<>oddílu**</span><span class="sxs-lookup"><span data-stu-id="298e2-113">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="298e2-114">Obsahuje deklaraci oddílu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="298e2-114">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="298e2-115">**\<oddílSkupina>**</span><span class="sxs-lookup"><span data-stu-id="298e2-115">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="298e2-116">Definuje obor názvů pro oddíly konfigurace.</span><span class="sxs-lookup"><span data-stu-id="298e2-116">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="298e2-117">**\<odebrat>**</span><span class="sxs-lookup"><span data-stu-id="298e2-117">**\<remove>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="298e2-118">Odebere předdefinovaný oddíl nebo skupinu oddílů.</span><span class="sxs-lookup"><span data-stu-id="298e2-118">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="298e2-119">**\<jasné>**</span><span class="sxs-lookup"><span data-stu-id="298e2-119">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="298e2-120">Vymaže všechny dříve definované oddíly a skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="298e2-120">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="298e2-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="298e2-121">Remarks</span></span>

<span data-ttu-id="298e2-122">Pokud je tento prvek v konfiguračním souboru, musí se jednat o první podřízený prvek \*\* \<prvku konfigurace>.\*\*</span><span class="sxs-lookup"><span data-stu-id="298e2-122">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="298e2-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="298e2-123">Example</span></span>

<span data-ttu-id="298e2-124">Následující příklad ukazuje, jak definovat konfigurační oddíl a definovat nastavení pro tento oddíl:</span><span class="sxs-lookup"><span data-stu-id="298e2-124">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="298e2-125">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="298e2-125">Configuration file</span></span>

<span data-ttu-id="298e2-126">Tento prvek lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače *(Machine.config*) a souborech *Web.config,* které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="298e2-126">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="298e2-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="298e2-127">See also</span></span>

- [<span data-ttu-id="298e2-128">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="298e2-128">Configuration file schema for the .NET Framework</span></span>](index.md)
