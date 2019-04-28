---
title: <add> – element pro NameValueSectionHandler a DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 9b421b4bab32c1aae7a6ba7d69b9f4aea2ab99a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705490"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="8dc91-102">\<Přidat > – element pro NameValueSectionHandler a DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="8dc91-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="8dc91-103">Přidá nastavení vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="8dc91-103">Adds custom application settings.</span></span> <span data-ttu-id="8dc91-104">Každý  **\<Přidat >** značka obsahuje dvojice klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="8dc91-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="8dc91-105">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="8dc91-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="8dc91-106">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="8dc91-106">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="8dc91-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span><span class="sxs-lookup"><span data-stu-id="8dc91-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="8dc91-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8dc91-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="8dc91-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="8dc91-109">Attributes</span></span>

| <span data-ttu-id="8dc91-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="8dc91-110">Attribute</span></span> | <span data-ttu-id="8dc91-111">Popis</span><span class="sxs-lookup"><span data-stu-id="8dc91-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="8dc91-112">**key**</span><span class="sxs-lookup"><span data-stu-id="8dc91-112">**key**</span></span>   | <span data-ttu-id="8dc91-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="8dc91-113">Required attribute.</span></span><br><br><span data-ttu-id="8dc91-114">Určuje název nastavení.</span><span class="sxs-lookup"><span data-stu-id="8dc91-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="8dc91-115">**value**</span><span class="sxs-lookup"><span data-stu-id="8dc91-115">**value**</span></span> | <span data-ttu-id="8dc91-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="8dc91-116">Required attribute.</span></span><br><br><span data-ttu-id="8dc91-117">Určuje hodnotu daného nastavení.</span><span class="sxs-lookup"><span data-stu-id="8dc91-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="8dc91-118">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="8dc91-118">Parent element</span></span>

| <span data-ttu-id="8dc91-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="8dc91-119">Element</span></span> | <span data-ttu-id="8dc91-120">Popis</span><span class="sxs-lookup"><span data-stu-id="8dc91-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="8dc91-121">**\<sectionName>** Element</span><span class="sxs-lookup"><span data-stu-id="8dc91-121">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="8dc91-122">Definuje nastavení pro vlastní konfigurační oddíly funkce, které používají <xref:System.Configuration.NameValueSectionHandler> a <xref:System.Configuration.DictionarySectionHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="8dc91-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="8dc91-123">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="8dc91-123">Child elements</span></span>

<span data-ttu-id="8dc91-124">Žádný</span><span class="sxs-lookup"><span data-stu-id="8dc91-124">None</span></span>

## <a name="example"></a><span data-ttu-id="8dc91-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="8dc91-125">Example</span></span>

<span data-ttu-id="8dc91-126">Následující příklad ukazuje, jak definovat vlastní konfigurační oddíl a použít  **\<Přidat >** element umístit do části nastavení:</span><span class="sxs-lookup"><span data-stu-id="8dc91-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="8dc91-127">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="8dc91-127">Configuration file</span></span>

<span data-ttu-id="8dc91-128">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="8dc91-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="8dc91-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8dc91-129">See also</span></span>

- [<span data-ttu-id="8dc91-130">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8dc91-130">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
