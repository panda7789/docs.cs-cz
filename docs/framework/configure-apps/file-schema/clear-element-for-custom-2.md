---
title: <clear>– element pro NameValueSectionHandler a DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
ms.openlocfilehash: f6d860f35d22002030ffa3d09dd0d8a96116bf5e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214746"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="5a568-102">\<clear>– element pro NameValueSectionHandler a DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="5a568-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="5a568-103">Vymaže všechna dříve definovaná nastavení v oddílu.</span><span class="sxs-lookup"><span data-stu-id="5a568-103">Clears all previously defined settings in a section.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="5a568-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a568-104">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="5a568-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="5a568-105">Attributes</span></span>

<span data-ttu-id="5a568-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="5a568-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="5a568-107">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="5a568-107">Parent element</span></span>

|     | <span data-ttu-id="5a568-108">Description</span><span class="sxs-lookup"><span data-stu-id="5a568-108">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="5a568-109">**\<sectionName>** Objekt</span><span class="sxs-lookup"><span data-stu-id="5a568-109">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="5a568-110">Definuje nastavení pro vlastní konfigurační oddíly, které používají <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> třídy a.</span><span class="sxs-lookup"><span data-stu-id="5a568-110">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="5a568-111">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="5a568-111">Child elements</span></span>

<span data-ttu-id="5a568-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="5a568-112">None</span></span>

## <a name="remarks"></a><span data-ttu-id="5a568-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a568-113">Remarks</span></span>

<span data-ttu-id="5a568-114">Pomocí **\<clear>** elementu můžete odebrat všechna nastavení z aplikace, která byla definována na vyšší úrovni v hierarchii konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="5a568-114">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="5a568-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a568-115">Example</span></span>

<span data-ttu-id="5a568-116">Tento příklad definuje konfigurační soubor počítače a konfigurační soubor aplikace a ukazuje, jak použít **\<clear>** element v konfiguračním souboru aplikace pro vymazání oddílů dříve definovaných v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="5a568-116">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="5a568-117">Následující kód konfiguračního souboru počítače deklaruje oddíl **\<mySection>** :</span><span class="sxs-lookup"><span data-stu-id="5a568-117">The following machine configuration file code declares the section **\<mySection>**:</span></span>

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

<span data-ttu-id="5a568-118">Následující kód konfiguračního souboru aplikace odebere všechna nastavení z **\<mySection>** .</span><span class="sxs-lookup"><span data-stu-id="5a568-118">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="5a568-119">Aplikace nemůže načíst žádná nastavení, která byla deklarována v v **\<mySection>** části konfiguračního souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="5a568-119">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="5a568-120">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="5a568-120">Configuration file</span></span>

<span data-ttu-id="5a568-121">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="5a568-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a568-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a568-122">See also</span></span>

- [<span data-ttu-id="5a568-123">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5a568-123">Configuration file schema for the .NET Framework</span></span>](index.md)
