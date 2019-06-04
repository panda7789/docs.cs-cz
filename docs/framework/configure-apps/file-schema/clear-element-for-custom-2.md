---
title: <clear> – element pro NameValueSectionHandler a DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: e5ab12150c5200dc346e950541443d5286f739c8
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301239"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="b4c30-102">\<Vymazat > – element pro NameValueSectionHandler a DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="b4c30-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="b4c30-103">Vymaže všechny dříve definované nastavení v oddílu.</span><span class="sxs-lookup"><span data-stu-id="b4c30-103">Clears all previously defined settings in a section.</span></span>

<span data-ttu-id="b4c30-104">[ **\<Konfigurace >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b4c30-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="b4c30-105">&nbsp;&nbsp;[ **\<sectionName>** ](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="b4c30-105">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="b4c30-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Vymazat >**</span><span class="sxs-lookup"><span data-stu-id="b4c30-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b4c30-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4c30-107">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="b4c30-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="b4c30-108">Attributes</span></span>

<span data-ttu-id="b4c30-109">Žádný</span><span class="sxs-lookup"><span data-stu-id="b4c30-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="b4c30-110">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="b4c30-110">Parent element</span></span>

|     | <span data-ttu-id="b4c30-111">Popis</span><span class="sxs-lookup"><span data-stu-id="b4c30-111">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="b4c30-112"> *\*\<sectionName>** Element</span><span class="sxs-lookup"><span data-stu-id="b4c30-112">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="b4c30-113">Definuje nastavení pro vlastní konfigurační oddíly funkce, které používají <xref:System.Configuration.NameValueSectionHandler> a <xref:System.Configuration.DictionarySectionHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="b4c30-113">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="b4c30-114">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="b4c30-114">Child elements</span></span>

<span data-ttu-id="b4c30-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="b4c30-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="b4c30-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4c30-116">Remarks</span></span>

<span data-ttu-id="b4c30-117">Můžete použít  **\<vymazat >** prvek, který chcete odebrat všechna nastavení z vaší aplikace, které byly definovány na vyšší úrovni v hierarchii konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="b4c30-117">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="b4c30-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="b4c30-118">Example</span></span>

<span data-ttu-id="b4c30-119">Tento příklad definuje konfigurační soubor počítače a konfigurační soubor aplikace a ukazuje způsob použití  **\<vymazat >** prvku v konfiguračním souboru aplikace, zrušte dříve definované v části konfigurační soubor počítače.</span><span class="sxs-lookup"><span data-stu-id="b4c30-119">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="b4c30-120">Následující počítače konfigurační soubor kód deklaruje části  **\<mySection >** :</span><span class="sxs-lookup"><span data-stu-id="b4c30-120">The following machine configuration file code declares the section **\<mySection>**:</span></span>

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

<span data-ttu-id="b4c30-121">Následující kód souboru konfigurace aplikace odebere všechna nastavení z  **\<mySection >** .</span><span class="sxs-lookup"><span data-stu-id="b4c30-121">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="b4c30-122">Aplikaci nelze načíst nastavení, které byly deklarovány v v  **\<mySection >** oddílu konfiguračního souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="b4c30-122">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="b4c30-123">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="b4c30-123">Configuration file</span></span>

<span data-ttu-id="b4c30-124">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="b4c30-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4c30-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4c30-125">See also</span></span>

- [<span data-ttu-id="b4c30-126">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b4c30-126">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
