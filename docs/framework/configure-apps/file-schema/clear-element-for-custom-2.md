---
title: element <clear> pro NameValueSectionHandler a DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fff5a5c2a523480f2eaebb127ec98ff6e9908acf
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088705"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="92bca-102">\<vymazat > elementu pro NameValueSectionHandler a DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="92bca-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="92bca-103">Vymaže všechna dříve definovaná nastavení v oddílu.</span><span class="sxs-lookup"><span data-stu-id="92bca-103">Clears all previously defined settings in a section.</span></span>

<span data-ttu-id="92bca-104">[ **\<configuration >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="92bca-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="92bca-105">&nbsp;&nbsp;[ **\<sectiongroup >** ](custom-element-2.md)</span><span class="sxs-lookup"><span data-stu-id="92bca-105">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)</span></span>\
<span data-ttu-id="92bca-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<vymazat >**</span><span class="sxs-lookup"><span data-stu-id="92bca-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="92bca-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92bca-107">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="92bca-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="92bca-108">Attributes</span></span>

<span data-ttu-id="92bca-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="92bca-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="92bca-110">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="92bca-110">Parent element</span></span>

|     | <span data-ttu-id="92bca-111">Popis</span><span class="sxs-lookup"><span data-stu-id="92bca-111">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="92bca-112"> **\<sectionGroup** Objekt</span><span class="sxs-lookup"><span data-stu-id="92bca-112">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="92bca-113">Definuje nastavení pro vlastní konfigurační oddíly, které používají třídy <xref:System.Configuration.NameValueSectionHandler> a <xref:System.Configuration.DictionarySectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="92bca-113">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="92bca-114">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="92bca-114">Child elements</span></span>

<span data-ttu-id="92bca-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="92bca-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="92bca-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="92bca-116">Remarks</span></span>

<span data-ttu-id="92bca-117">Pomocí elementu **\<clear >** můžete odebrat všechna nastavení z aplikace, která byla definována na vyšší úrovni v hierarchii konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="92bca-117">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="92bca-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="92bca-118">Example</span></span>

<span data-ttu-id="92bca-119">Tento příklad definuje konfigurační soubor počítače a konfigurační soubor aplikace a ukazuje, jak použít **\<clear >** elementu v konfiguračním souboru aplikace pro vymazání oddílů dříve definovaných v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="92bca-119">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="92bca-120">Následující kód konfiguračního souboru počítače deklaruje oddíl **\<mySection >** :</span><span class="sxs-lookup"><span data-stu-id="92bca-120">The following machine configuration file code declares the section **\<mySection>**:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

<span data-ttu-id="92bca-121">Následující kód konfiguračního souboru aplikace odebere všechna nastavení z **\<mySection >** .</span><span class="sxs-lookup"><span data-stu-id="92bca-121">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="92bca-122">Aplikace nemůže načíst žádná nastavení, která byla deklarována v v části **\<mySection** konfiguračního souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="92bca-122">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="92bca-123">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="92bca-123">Configuration file</span></span>

<span data-ttu-id="92bca-124">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="92bca-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="92bca-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92bca-125">See also</span></span>

- [<span data-ttu-id="92bca-126">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="92bca-126">Configuration file schema for the .NET Framework</span></span>](index.md)
