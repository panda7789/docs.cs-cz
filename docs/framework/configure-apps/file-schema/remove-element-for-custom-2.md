---
title: <remove> – element pro NameValueSectionHandler a DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: guardrex
ms.author: mairaw
ms.openlocfilehash: c86d231a4e3e8e15df94017a6ca461b365643ea5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705088"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="455fd-102">\<Odebrat > – element pro NameValueSectionHandler a DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="455fd-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="455fd-103">Odstraní dříve definované nastavení.</span><span class="sxs-lookup"><span data-stu-id="455fd-103">Removes a previously defined setting.</span></span>

<span data-ttu-id="455fd-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="455fd-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="455fd-105">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="455fd-105">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="455fd-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="455fd-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="455fd-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="455fd-107">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="455fd-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="455fd-108">Attribute</span></span>

|           | <span data-ttu-id="455fd-109">Popis</span><span class="sxs-lookup"><span data-stu-id="455fd-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="455fd-110">**key**</span><span class="sxs-lookup"><span data-stu-id="455fd-110">**key**</span></span>   | <span data-ttu-id="455fd-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="455fd-111">Required attribute.</span></span><br><br><span data-ttu-id="455fd-112">Určuje název tohoto nastavení odebrat.</span><span class="sxs-lookup"><span data-stu-id="455fd-112">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="455fd-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="455fd-113">Parent element</span></span>

| <span data-ttu-id="455fd-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="455fd-114">Element</span></span> | <span data-ttu-id="455fd-115">Popis</span><span class="sxs-lookup"><span data-stu-id="455fd-115">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="455fd-116">**\<sectionName>** Element</span><span class="sxs-lookup"><span data-stu-id="455fd-116">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="455fd-117">Definuje nastavení pro vlastní konfigurační oddíly funkce, které používají <xref:System.Configuration.NameValueSectionHandler> a <xref:System.Configuration.DictionarySectionHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="455fd-117">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="455fd-118">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="455fd-118">Child elements</span></span>

<span data-ttu-id="455fd-119">Žádný</span><span class="sxs-lookup"><span data-stu-id="455fd-119">None</span></span>

## <a name="remarks"></a><span data-ttu-id="455fd-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="455fd-120">Remarks</span></span>

<span data-ttu-id="455fd-121">Můžete použít  **\<odebrat >** prvek, který chcete odebrat nastavení z vaší aplikace, které byly definovány na vyšší úrovni v hierarchii konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="455fd-121">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="455fd-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="455fd-122">Example</span></span>

<span data-ttu-id="455fd-123">Následující příklad ukazuje způsob použití  **\<odebrat >** prvku v konfiguračním souboru aplikace k odebrání nastavení dříve definovaných v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="455fd-123">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="455fd-124">Následující počítače konfigurační soubor kód deklaruje části  **\<mySection >** a přidá dvě nastavení `key1` a `key2`, do něj:</span><span class="sxs-lookup"><span data-stu-id="455fd-124">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

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

<span data-ttu-id="455fd-125">Následující kód souboru konfigurace aplikace odebere `key2` nastavení z  **\<mySection >**:</span><span class="sxs-lookup"><span data-stu-id="455fd-125">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="455fd-126">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="455fd-126">Configuration file</span></span>

<span data-ttu-id="455fd-127">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="455fd-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="455fd-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="455fd-128">See also</span></span>

- [<span data-ttu-id="455fd-129">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="455fd-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
