---
title: <remove> – element pro <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
ms.openlocfilehash: 6991e3f73ac180fc690ec48e1a0d15f40c915733
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154527"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="13207-102">\<remove> – element pro \<configSections></span><span class="sxs-lookup"><span data-stu-id="13207-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="13207-103">Odebere předdefinovanou sekci nebo skupinu oddílů.</span><span class="sxs-lookup"><span data-stu-id="13207-103">Removes a predefined section or section group.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="13207-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13207-104">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="13207-105">Atribut</span><span class="sxs-lookup"><span data-stu-id="13207-105">Attribute</span></span>

|           | <span data-ttu-id="13207-106">Popis</span><span class="sxs-lookup"><span data-stu-id="13207-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="13207-107">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="13207-107">**name**</span></span>  | <span data-ttu-id="13207-108">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="13207-108">Required attribute.</span></span><br><br><span data-ttu-id="13207-109">Určuje název oddílu nebo skupiny oddílů, které se mají odebrat.</span><span class="sxs-lookup"><span data-stu-id="13207-109">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="13207-110">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="13207-110">Parent element</span></span>

|     | <span data-ttu-id="13207-111">Description</span><span class="sxs-lookup"><span data-stu-id="13207-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="13207-112">**\<configSections>** Objekt</span><span class="sxs-lookup"><span data-stu-id="13207-112">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="13207-113">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="13207-113">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="13207-114">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="13207-114">Child elements</span></span>

<span data-ttu-id="13207-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="13207-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="13207-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13207-116">Remarks</span></span>

<span data-ttu-id="13207-117">Element lze použít **\<remove>** k odebrání oddílů a skupin oddílů z aplikace, které byly definovány na vyšší úrovni v hierarchii konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="13207-117">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="13207-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="13207-118">Example</span></span>

<span data-ttu-id="13207-119">Následující příklad ukazuje, jak použít **\<remove>** element v konfiguračním souboru aplikace k odebrání oddílu dříve definovaného v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="13207-119">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="13207-120">Následující kód konfiguračního souboru počítače deklaruje oddíl **\<sampleSection>** :</span><span class="sxs-lookup"><span data-stu-id="13207-120">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

```xml
<!-- Machine.config file -->
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

<span data-ttu-id="13207-121">Následující kód konfiguračního souboru aplikace tuto část odstraní **\<sampleSection>** .</span><span class="sxs-lookup"><span data-stu-id="13207-121">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="13207-122">Po odebrání nemůže aplikace načíst nastavení v **\<sampleSection>** .</span><span class="sxs-lookup"><span data-stu-id="13207-122">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="13207-123">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="13207-123">Configuration file</span></span>

<span data-ttu-id="13207-124">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="13207-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="13207-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="13207-125">See also</span></span>

- [<span data-ttu-id="13207-126">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="13207-126">Configuration file schema for the .NET Framework</span></span>](index.md)
