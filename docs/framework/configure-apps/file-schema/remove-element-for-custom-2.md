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
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267414"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="0ddf1-102">\<Odebrat > – element pro NameValueSectionHandler a DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="0ddf1-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="0ddf1-103">Odstraní dříve definované nastavení.</span><span class="sxs-lookup"><span data-stu-id="0ddf1-103">Removes a previously defined setting.</span></span>

<span data-ttu-id="0ddf1-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="0ddf1-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="0ddf1-105">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="0ddf1-105">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="0ddf1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="0ddf1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="0ddf1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ddf1-107">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="0ddf1-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="0ddf1-108">Attribute</span></span>

|           | <span data-ttu-id="0ddf1-109">Popis</span><span class="sxs-lookup"><span data-stu-id="0ddf1-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="0ddf1-110">**key**</span><span class="sxs-lookup"><span data-stu-id="0ddf1-110">**key**</span></span>   | <span data-ttu-id="0ddf1-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="0ddf1-111">Required attribute.</span></span><br><br><span data-ttu-id="0ddf1-112">Určuje název tohoto nastavení odebrat.</span><span class="sxs-lookup"><span data-stu-id="0ddf1-112">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="0ddf1-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="0ddf1-113">Parent element</span></span>

| <span data-ttu-id="0ddf1-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="0ddf1-114">Element</span></span> | <span data-ttu-id="0ddf1-115">Popis</span><span class="sxs-lookup"><span data-stu-id="0ddf1-115">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="0ddf1-116">**\<sectionName>** Element</span><span class="sxs-lookup"><span data-stu-id="0ddf1-116">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="0ddf1-117">Definuje nastavení pro vlastní konfigurační oddíly funkce, které používají <xref:System.Configuration.NameValueSectionHandler> a <xref:System.Configuration.DictionarySectionHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="0ddf1-117">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="0ddf1-118">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="0ddf1-118">Child elements</span></span>

<span data-ttu-id="0ddf1-119">Žádná</span><span class="sxs-lookup"><span data-stu-id="0ddf1-119">None</span></span>

## <a name="remarks"></a><span data-ttu-id="0ddf1-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ddf1-120">Remarks</span></span>

<span data-ttu-id="0ddf1-121">Můžete použít  **\<odebrat >** prvek, který chcete odebrat nastavení z vaší aplikace, které byly definovány na vyšší úrovni v hierarchii konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="0ddf1-121">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="0ddf1-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="0ddf1-122">Example</span></span>

<span data-ttu-id="0ddf1-123">Následující příklad ukazuje způsob použití  **\<odebrat >** prvku v konfiguračním souboru aplikace k odebrání nastavení dříve definovaných v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="0ddf1-123">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="0ddf1-124">Následující počítače konfigurační soubor kód deklaruje části  **\<mySection >** a přidá dvě nastavení `key1` a `key2`, do něj:</span><span class="sxs-lookup"><span data-stu-id="0ddf1-124">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

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

<span data-ttu-id="0ddf1-125">Následující kód souboru konfigurace aplikace odebere `key2` nastavení z  **\<mySection >**:</span><span class="sxs-lookup"><span data-stu-id="0ddf1-125">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="0ddf1-126">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="0ddf1-126">Configuration file</span></span>

<span data-ttu-id="0ddf1-127">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="0ddf1-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ddf1-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ddf1-128">See also</span></span>

- [<span data-ttu-id="0ddf1-129">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0ddf1-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
