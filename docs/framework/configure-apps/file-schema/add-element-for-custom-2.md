---
title: <add> – element pro NameValueSectionHandler a DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 3bbe4ad6559e324db5853b95e797f50a7b908dcb
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301435"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="df056-102">\<Přidat > – element pro NameValueSectionHandler a DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="df056-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="df056-103">Přidá nastavení vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="df056-103">Adds custom application settings.</span></span> <span data-ttu-id="df056-104">Každý  **\<Přidat >** značka obsahuje dvojice klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="df056-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="df056-105">[ **\<Konfigurace >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="df056-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="df056-106">&nbsp;&nbsp;[ **\<sectionName>** ](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="df056-106">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="df056-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**</span><span class="sxs-lookup"><span data-stu-id="df056-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="df056-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df056-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="df056-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="df056-109">Attributes</span></span>

| <span data-ttu-id="df056-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="df056-110">Attribute</span></span> | <span data-ttu-id="df056-111">Popis</span><span class="sxs-lookup"><span data-stu-id="df056-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="df056-112">**key**</span><span class="sxs-lookup"><span data-stu-id="df056-112">**key**</span></span>   | <span data-ttu-id="df056-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="df056-113">Required attribute.</span></span><br><br><span data-ttu-id="df056-114">Určuje název nastavení.</span><span class="sxs-lookup"><span data-stu-id="df056-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="df056-115">**value**</span><span class="sxs-lookup"><span data-stu-id="df056-115">**value**</span></span> | <span data-ttu-id="df056-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="df056-116">Required attribute.</span></span><br><br><span data-ttu-id="df056-117">Určuje hodnotu daného nastavení.</span><span class="sxs-lookup"><span data-stu-id="df056-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="df056-118">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="df056-118">Parent element</span></span>

| <span data-ttu-id="df056-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="df056-119">Element</span></span> | <span data-ttu-id="df056-120">Popis</span><span class="sxs-lookup"><span data-stu-id="df056-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="df056-121"> *\*\<sectionName>** Element</span><span class="sxs-lookup"><span data-stu-id="df056-121">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="df056-122">Definuje nastavení pro vlastní konfigurační oddíly funkce, které používají <xref:System.Configuration.NameValueSectionHandler> a <xref:System.Configuration.DictionarySectionHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="df056-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="df056-123">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="df056-123">Child elements</span></span>

<span data-ttu-id="df056-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="df056-124">None</span></span>

## <a name="example"></a><span data-ttu-id="df056-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="df056-125">Example</span></span>

<span data-ttu-id="df056-126">Následující příklad ukazuje, jak definovat vlastní konfigurační oddíl a použít  **\<Přidat >** element umístit do části nastavení:</span><span class="sxs-lookup"><span data-stu-id="df056-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="df056-127">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="df056-127">Configuration file</span></span>

<span data-ttu-id="df056-128">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="df056-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="df056-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="df056-129">See also</span></span>

- [<span data-ttu-id="df056-130">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="df056-130">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
