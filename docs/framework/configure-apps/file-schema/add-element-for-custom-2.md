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
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278275"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="44676-102">\<Přidat > – element pro NameValueSectionHandler a DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="44676-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="44676-103">Přidá nastavení vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="44676-103">Adds custom application settings.</span></span> <span data-ttu-id="44676-104">Každý  **\<Přidat >** značka obsahuje dvojice klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="44676-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="44676-105">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="44676-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="44676-106">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="44676-106">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="44676-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span><span class="sxs-lookup"><span data-stu-id="44676-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="44676-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44676-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="44676-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="44676-109">Attributes</span></span>

| <span data-ttu-id="44676-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="44676-110">Attribute</span></span> | <span data-ttu-id="44676-111">Popis</span><span class="sxs-lookup"><span data-stu-id="44676-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="44676-112">**key**</span><span class="sxs-lookup"><span data-stu-id="44676-112">**key**</span></span>   | <span data-ttu-id="44676-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="44676-113">Required attribute.</span></span><br><br><span data-ttu-id="44676-114">Určuje název nastavení.</span><span class="sxs-lookup"><span data-stu-id="44676-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="44676-115">**value**</span><span class="sxs-lookup"><span data-stu-id="44676-115">**value**</span></span> | <span data-ttu-id="44676-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="44676-116">Required attribute.</span></span><br><br><span data-ttu-id="44676-117">Určuje hodnotu daného nastavení.</span><span class="sxs-lookup"><span data-stu-id="44676-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="44676-118">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="44676-118">Parent element</span></span>

| <span data-ttu-id="44676-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="44676-119">Element</span></span> | <span data-ttu-id="44676-120">Popis</span><span class="sxs-lookup"><span data-stu-id="44676-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="44676-121">**\<sectionName>** Element</span><span class="sxs-lookup"><span data-stu-id="44676-121">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="44676-122">Definuje nastavení pro vlastní konfigurační oddíly funkce, které používají <xref:System.Configuration.NameValueSectionHandler> a <xref:System.Configuration.DictionarySectionHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="44676-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="44676-123">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="44676-123">Child elements</span></span>

<span data-ttu-id="44676-124">Žádná</span><span class="sxs-lookup"><span data-stu-id="44676-124">None</span></span>

## <a name="example"></a><span data-ttu-id="44676-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="44676-125">Example</span></span>

<span data-ttu-id="44676-126">Následující příklad ukazuje, jak definovat vlastní konfigurační oddíl a použít  **\<Přidat >** element umístit do části nastavení:</span><span class="sxs-lookup"><span data-stu-id="44676-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="44676-127">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="44676-127">Configuration file</span></span>

<span data-ttu-id="44676-128">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="44676-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="44676-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44676-129">See also</span></span>

- [<span data-ttu-id="44676-130">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="44676-130">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
