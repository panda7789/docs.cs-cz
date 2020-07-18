---
title: <configSections> – element pro <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 1e4bb7a7cfb0b140ca6d13c162708c3c30bd496d
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441684"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="a8f83-102">\<configSections> – element pro \<configuration></span><span class="sxs-lookup"><span data-stu-id="a8f83-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="a8f83-103">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a8f83-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="a8f83-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="a8f83-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="a8f83-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="a8f83-105">Attributes</span></span>

<span data-ttu-id="a8f83-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="a8f83-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="a8f83-107">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="a8f83-107">Parent element</span></span>

|     | <span data-ttu-id="a8f83-108">Popis</span><span class="sxs-lookup"><span data-stu-id="a8f83-108">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="a8f83-109">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a8f83-109">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="a8f83-110">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="a8f83-110">Child elements</span></span>

|     | <span data-ttu-id="a8f83-111">Popis</span><span class="sxs-lookup"><span data-stu-id="a8f83-111">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="a8f83-112">Obsahuje deklaraci konfiguračního oddílu.</span><span class="sxs-lookup"><span data-stu-id="a8f83-112">Contains a configuration section declaration.</span></span> |
| [**\<sectionGroup>**](sectiongroup-element-for-configsections.md) | <span data-ttu-id="a8f83-113">Definuje obor názvů pro konfigurační oddíly.</span><span class="sxs-lookup"><span data-stu-id="a8f83-113">Defines a namespace for configuration sections.</span></span> |

## <a name="remarks"></a><span data-ttu-id="a8f83-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8f83-114">Remarks</span></span>

<span data-ttu-id="a8f83-115">Pokud je tento prvek v konfiguračním souboru, musí být prvním podřízeným elementem **\<configuration>** elementu.</span><span class="sxs-lookup"><span data-stu-id="a8f83-115">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="a8f83-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8f83-116">Example</span></span>

<span data-ttu-id="a8f83-117">Následující příklad ukazuje, jak definovat konfigurační oddíl a definovat nastavení pro tuto část:</span><span class="sxs-lookup"><span data-stu-id="a8f83-117">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="a8f83-118">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="a8f83-118">Configuration file</span></span>

<span data-ttu-id="a8f83-119">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*) a *Web.config* soubory, které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="a8f83-119">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8f83-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8f83-120">See also</span></span>

- [<span data-ttu-id="a8f83-121">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a8f83-121">Configuration file schema for the .NET Framework</span></span>](index.md)
