---
title: '&lt;Vymazat&gt; – element pro &lt;configSections&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 9439e2ac7634b242c9f847346f7dcf265d6ab419
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678002"
---
# <a name="clear-element-for-configsections"></a><span data-ttu-id="ad005-102">\<Vymazat > – element pro \<configSections ></span><span class="sxs-lookup"><span data-stu-id="ad005-102">\<clear> element for \<configSections></span></span>

<span data-ttu-id="ad005-103">Vymaže všechny dříve definované oddíly a skupin oddílů.</span><span class="sxs-lookup"><span data-stu-id="ad005-103">Clears all previously defined sections and section groups.</span></span>

<span data-ttu-id="ad005-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="ad005-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="ad005-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="ad005-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="ad005-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Vymazat >**</span><span class="sxs-lookup"><span data-stu-id="ad005-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ad005-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad005-107">Syntax</span></span>

```xml
<clear/>
```

## <a name="attribute"></a><span data-ttu-id="ad005-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="ad005-108">Attribute</span></span>

|           | <span data-ttu-id="ad005-109">Popis</span><span class="sxs-lookup"><span data-stu-id="ad005-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="ad005-110">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="ad005-110">**name**</span></span>  | <span data-ttu-id="ad005-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="ad005-111">Required attribute.</span></span><br><br><span data-ttu-id="ad005-112">Určuje název sekce nebo skupiny části odebrat.</span><span class="sxs-lookup"><span data-stu-id="ad005-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="ad005-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="ad005-113">Parent element</span></span>

|     | <span data-ttu-id="ad005-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ad005-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ad005-115">**\<configSections>** Element</span><span class="sxs-lookup"><span data-stu-id="ad005-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="ad005-116">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ad005-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="ad005-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="ad005-117">Child elements</span></span>

<span data-ttu-id="ad005-118">Žádná</span><span class="sxs-lookup"><span data-stu-id="ad005-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="ad005-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad005-119">Remarks</span></span>

<span data-ttu-id="ad005-120"> *\*\<Vymazat >** element odebere všechny oddíly a skupiny oddílů z vaší aplikace, které byly dříve definovány v aktuálním konfiguračním souboru nebo na vyšší úrovni v hierarchii konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="ad005-120">The **\<clear>** element removes all sections and section groups from your application that were defined earlier in the current configuration file or at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="ad005-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad005-121">Example</span></span>

<span data-ttu-id="ad005-122">Tento příklad definuje konfigurační soubor počítače a konfigurační soubor aplikace a ukazuje způsob použití  **\<vymazat >** prvku v konfiguračním souboru aplikace, zrušte dříve definované v části konfigurační soubor počítače.</span><span class="sxs-lookup"><span data-stu-id="ad005-122">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="ad005-123">Následující počítače konfigurační soubor kód deklaruje dvě části  **\<sampleSection >** a  **\<anotherSampleSection >**, které jsou přečteny před aplikace konfigurační soubor:</span><span class="sxs-lookup"><span data-stu-id="ad005-123">The following machine configuration file code declares two sections, **\<sampleSection>** and **\<anotherSampleSection>**, which are read before the application configuration file:</span></span>

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

<span data-ttu-id="ad005-124">Následující kód souboru konfigurace aplikace vymaže všechny dříve deklarovaný oddíly.</span><span class="sxs-lookup"><span data-stu-id="ad005-124">The following application configuration file code clears all previously declared sections.</span></span> <span data-ttu-id="ad005-125">Aplikaci nejde použít nebo načíst nastavení v některém z části, které byly deklarovány v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="ad005-125">The application cannot use or retrieve settings in either of the sections that were declared in the machine configuration file.</span></span> <span data-ttu-id="ad005-126">Ale můžete použít nastavení z  **\<anotherSection >** vzhledem k tomu, že jde o po  **\<vymazat >** elementu.</span><span class="sxs-lookup"><span data-stu-id="ad005-126">However, it can use settings from **\<anotherSection>** because it comes after the **\<clear>** element.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="ad005-127">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="ad005-127">Configuration file</span></span>

<span data-ttu-id="ad005-128">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="ad005-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad005-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad005-129">See also</span></span>

- [<span data-ttu-id="ad005-130">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ad005-130">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
