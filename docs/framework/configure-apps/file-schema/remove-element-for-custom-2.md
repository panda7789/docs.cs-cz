---
title: element <remove> pro NameValueSectionHandler a DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6cdd5833e14da1ab5185e56dce1190adfee4a2bf
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089029"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="868b0-102">\<odebrat > element pro NameValueSectionHandler a DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="868b0-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="868b0-103">Odebere dříve definované nastavení.</span><span class="sxs-lookup"><span data-stu-id="868b0-103">Removes a previously defined setting.</span></span>

<span data-ttu-id="868b0-104">[ **\<configuration >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="868b0-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="868b0-105">&nbsp;&nbsp;[ **\<sectiongroup >** ](custom-element-2.md)</span><span class="sxs-lookup"><span data-stu-id="868b0-105">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)</span></span>\
<span data-ttu-id="868b0-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<odebrat >**</span><span class="sxs-lookup"><span data-stu-id="868b0-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="868b0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="868b0-107">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="868b0-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="868b0-108">Attribute</span></span>

|           | <span data-ttu-id="868b0-109">Popis</span><span class="sxs-lookup"><span data-stu-id="868b0-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="868b0-110">**zkrat**</span><span class="sxs-lookup"><span data-stu-id="868b0-110">**key**</span></span>   | <span data-ttu-id="868b0-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="868b0-111">Required attribute.</span></span><br><br><span data-ttu-id="868b0-112">Určuje název nastavení, které se má odebrat.</span><span class="sxs-lookup"><span data-stu-id="868b0-112">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="868b0-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="868b0-113">Parent element</span></span>

| <span data-ttu-id="868b0-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="868b0-114">Element</span></span> | <span data-ttu-id="868b0-115">Popis</span><span class="sxs-lookup"><span data-stu-id="868b0-115">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="868b0-116"> **\<sectionGroup** Objekt</span><span class="sxs-lookup"><span data-stu-id="868b0-116">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="868b0-117">Definuje nastavení pro vlastní konfigurační oddíly, které používají třídy <xref:System.Configuration.NameValueSectionHandler> a <xref:System.Configuration.DictionarySectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="868b0-117">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="868b0-118">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="868b0-118">Child elements</span></span>

<span data-ttu-id="868b0-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="868b0-119">None</span></span>

## <a name="remarks"></a><span data-ttu-id="868b0-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="868b0-120">Remarks</span></span>

<span data-ttu-id="868b0-121">Pomocí elementu **\<remove >** můžete odebrat nastavení z aplikace, které bylo definováno na vyšší úrovni v hierarchii konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="868b0-121">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="868b0-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="868b0-122">Example</span></span>

<span data-ttu-id="868b0-123">Následující příklad ukazuje, jak použít **\<odebrat >** elementu v konfiguračním souboru aplikace k odebrání nastavení dříve definovaného v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="868b0-123">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="868b0-124">Následující kód konfiguračního souboru počítače deklaruje oddíl **\<mySection >** a přidává do něj dvě nastavení, `key1` a `key2`:</span><span class="sxs-lookup"><span data-stu-id="868b0-124">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

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

<span data-ttu-id="868b0-125">Následující kód konfiguračního souboru aplikace odebere `key2` nastavení z **\<mySection >** :</span><span class="sxs-lookup"><span data-stu-id="868b0-125">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="868b0-126">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="868b0-126">Configuration file</span></span>

<span data-ttu-id="868b0-127">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="868b0-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="868b0-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="868b0-128">See also</span></span>

- [<span data-ttu-id="868b0-129">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="868b0-129">Configuration file schema for the .NET Framework</span></span>](index.md)
