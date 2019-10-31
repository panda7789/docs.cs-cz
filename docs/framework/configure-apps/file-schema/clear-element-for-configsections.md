---
title: <clear> – element pro <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a45572d0dcb2737558e11f5c38ac2ccc338c754a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119087"
---
# <a name="clear-element-for-configsections"></a><span data-ttu-id="ae84b-102">\<Clear > element pro \<configSections ></span><span class="sxs-lookup"><span data-stu-id="ae84b-102">\<clear> element for \<configSections></span></span>

<span data-ttu-id="ae84b-103">Vymaže všechny dříve definované oddíly a skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="ae84b-103">Clears all previously defined sections and section groups.</span></span>

<span data-ttu-id="ae84b-104">[**konfigurační >\<** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="ae84b-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="ae84b-105">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="ae84b-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="ae84b-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<vymazat >**</span><span class="sxs-lookup"><span data-stu-id="ae84b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ae84b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae84b-107">Syntax</span></span>

```xml
<clear/>
```

## <a name="attribute"></a><span data-ttu-id="ae84b-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="ae84b-108">Attribute</span></span>

|           | <span data-ttu-id="ae84b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="ae84b-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="ae84b-110">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="ae84b-110">**name**</span></span>  | <span data-ttu-id="ae84b-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="ae84b-111">Required attribute.</span></span><br><br><span data-ttu-id="ae84b-112">Určuje název oddílu nebo skupiny oddílů, které se mají odebrat.</span><span class="sxs-lookup"><span data-stu-id="ae84b-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="ae84b-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="ae84b-113">Parent element</span></span>

|     | <span data-ttu-id="ae84b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ae84b-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ae84b-115"> **\<configSections >** Objekt</span><span class="sxs-lookup"><span data-stu-id="ae84b-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="ae84b-116">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ae84b-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="ae84b-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="ae84b-117">Child elements</span></span>

<span data-ttu-id="ae84b-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="ae84b-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="ae84b-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ae84b-119">Remarks</span></span>

<span data-ttu-id="ae84b-120">Element **\<clear >** odebere všechny oddíly a skupiny oddílů z vaší aplikace, které byly definovány dříve v aktuálním konfiguračním souboru nebo na vyšší úrovni v hierarchii konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="ae84b-120">The **\<clear>** element removes all sections and section groups from your application that were defined earlier in the current configuration file or at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="ae84b-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae84b-121">Example</span></span>

<span data-ttu-id="ae84b-122">Tento příklad definuje konfigurační soubor počítače a konfigurační soubor aplikace a ukazuje, jak použít **\<clear >** elementu v konfiguračním souboru aplikace pro vymazání oddílů dříve definovaných v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="ae84b-122">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="ae84b-123">Následující kód konfiguračního souboru počítače deklaruje dva oddíly **\<sampleSection >** a **\<anotherSampleSection >** , které jsou čteny před konfiguračním souborem aplikace:</span><span class="sxs-lookup"><span data-stu-id="ae84b-123">The following machine configuration file code declares two sections, **\<sampleSection>** and **\<anotherSampleSection>**, which are read before the application configuration file:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
    <section name="anotherSampleSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

<span data-ttu-id="ae84b-124">Následující kód konfiguračního souboru aplikace vymaže všechny dříve deklarované oddíly.</span><span class="sxs-lookup"><span data-stu-id="ae84b-124">The following application configuration file code clears all previously declared sections.</span></span> <span data-ttu-id="ae84b-125">Aplikace nemůže použít nebo načíst nastavení v některé z oddílů, které byly deklarovány v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="ae84b-125">The application cannot use or retrieve settings in either of the sections that were declared in the machine configuration file.</span></span> <span data-ttu-id="ae84b-126">Může však použít nastavení z **\<anotherSection >** , protože se nachází po **\<jasný >** element.</span><span class="sxs-lookup"><span data-stu-id="ae84b-126">However, it can use settings from **\<anotherSection>** because it comes after the **\<clear>** element.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <clear/>
    <section name="anotherSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <anotherSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="ae84b-127">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="ae84b-127">Configuration file</span></span>

<span data-ttu-id="ae84b-128">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="ae84b-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae84b-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae84b-129">See also</span></span>

- [<span data-ttu-id="ae84b-130">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ae84b-130">Configuration file schema for the .NET Framework</span></span>](index.md)
