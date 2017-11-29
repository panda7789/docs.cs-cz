---
title: "&lt;Přidat&gt; element NameValueSectionHandler a DictionarySectionHandler"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e9dc671f0df9034410d20fdf69862884d6b3b300
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="aebd0-102">\<Přidat > element NameValueSectionHandler a DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="aebd0-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="aebd0-103">Přidá nastavení vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="aebd0-103">Adds custom application settings.</span></span> <span data-ttu-id="aebd0-104">Každý  **\<Přidat >** značka obsahuje dvojice klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="aebd0-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="aebd0-105">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="aebd0-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="aebd0-106">&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="aebd0-106">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="aebd0-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="aebd0-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="aebd0-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aebd0-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="aebd0-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="aebd0-109">Attributes</span></span>

| <span data-ttu-id="aebd0-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="aebd0-110">Attribute</span></span> | <span data-ttu-id="aebd0-111">Popis</span><span class="sxs-lookup"><span data-stu-id="aebd0-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="aebd0-112">**klíč**</span><span class="sxs-lookup"><span data-stu-id="aebd0-112">**key**</span></span>   | <span data-ttu-id="aebd0-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="aebd0-113">Required attribute.</span></span><br><br><span data-ttu-id="aebd0-114">Určuje název nastavení.</span><span class="sxs-lookup"><span data-stu-id="aebd0-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="aebd0-115">**Hodnota**</span><span class="sxs-lookup"><span data-stu-id="aebd0-115">**value**</span></span> | <span data-ttu-id="aebd0-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="aebd0-116">Required attribute.</span></span><br><br><span data-ttu-id="aebd0-117">Určuje hodnotu nastavení.</span><span class="sxs-lookup"><span data-stu-id="aebd0-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="aebd0-118">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="aebd0-118">Parent element</span></span>

| <span data-ttu-id="aebd0-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="aebd0-119">Element</span></span> | <span data-ttu-id="aebd0-120">Popis</span><span class="sxs-lookup"><span data-stu-id="aebd0-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="aebd0-121">**\<sectionName >** – Element</span><span class="sxs-lookup"><span data-stu-id="aebd0-121">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="aebd0-122">Definuje nastavení pro vlastní konfiguračních oddílů, které používají <xref:System.Configuration.NameValueSectionHandler> a <xref:System.Configuration.DictionarySectionHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="aebd0-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="aebd0-123">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="aebd0-123">Child elements</span></span>

<span data-ttu-id="aebd0-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="aebd0-124">None</span></span>

## <a name="example"></a><span data-ttu-id="aebd0-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="aebd0-125">Example</span></span>

<span data-ttu-id="aebd0-126">Následující příklad ukazuje, jak definovat vlastní oddíl konfigurace a použít  **\<Přidat >** element převést nastavení do části:</span><span class="sxs-lookup"><span data-stu-id="aebd0-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="aebd0-127">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="aebd0-127">Configuration file</span></span>

<span data-ttu-id="aebd0-128">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="aebd0-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="aebd0-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="aebd0-129">See also</span></span>

[<span data-ttu-id="aebd0-130">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="aebd0-130">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
