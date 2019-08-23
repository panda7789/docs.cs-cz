---
title: <add>– element pro NameValueSectionHandler a DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: ec6d5045580e887de5f05a05c8f39fa62c6e3f2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921341"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="b99dc-102">\<Přidat > element pro NameValueSectionHandler a DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="b99dc-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="b99dc-103">Přidá vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="b99dc-103">Adds custom application settings.</span></span> <span data-ttu-id="b99dc-104">Každá značka přidání > obsahuje dvojici klíč/hodnota.  **\<**</span><span class="sxs-lookup"><span data-stu-id="b99dc-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="b99dc-105">[ **\<> Konfigurace**](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b99dc-105">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="b99dc-106">&nbsp;&nbsp;[ **\<sectionName>** ](custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="b99dc-106">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md) </span></span>  
<span data-ttu-id="b99dc-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="b99dc-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b99dc-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b99dc-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="b99dc-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="b99dc-109">Attributes</span></span>

| <span data-ttu-id="b99dc-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="b99dc-110">Attribute</span></span> | <span data-ttu-id="b99dc-111">Popis</span><span class="sxs-lookup"><span data-stu-id="b99dc-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="b99dc-112">**key**</span><span class="sxs-lookup"><span data-stu-id="b99dc-112">**key**</span></span>   | <span data-ttu-id="b99dc-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="b99dc-113">Required attribute.</span></span><br><br><span data-ttu-id="b99dc-114">Určuje název nastavení.</span><span class="sxs-lookup"><span data-stu-id="b99dc-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="b99dc-115">**value**</span><span class="sxs-lookup"><span data-stu-id="b99dc-115">**value**</span></span> | <span data-ttu-id="b99dc-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="b99dc-116">Required attribute.</span></span><br><br><span data-ttu-id="b99dc-117">Určuje hodnotu nastavení.</span><span class="sxs-lookup"><span data-stu-id="b99dc-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="b99dc-118">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="b99dc-118">Parent element</span></span>

| <span data-ttu-id="b99dc-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="b99dc-119">Element</span></span> | <span data-ttu-id="b99dc-120">Popis</span><span class="sxs-lookup"><span data-stu-id="b99dc-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="b99dc-121"> **sectionGroup>\<** element</span><span class="sxs-lookup"><span data-stu-id="b99dc-121">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="b99dc-122">Definuje nastavení pro vlastní konfigurační oddíly, které používají <xref:System.Configuration.NameValueSectionHandler> třídy <xref:System.Configuration.DictionarySectionHandler> a.</span><span class="sxs-lookup"><span data-stu-id="b99dc-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="b99dc-123">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="b99dc-123">Child elements</span></span>

<span data-ttu-id="b99dc-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="b99dc-124">None</span></span>

## <a name="example"></a><span data-ttu-id="b99dc-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="b99dc-125">Example</span></span>

<span data-ttu-id="b99dc-126">Následující příklad ukazuje, jak definovat vlastní konfigurační oddíl a použít  **\<element add >** k umístění nastavení do oddílu:</span><span class="sxs-lookup"><span data-stu-id="b99dc-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="b99dc-127">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="b99dc-127">Configuration file</span></span>

<span data-ttu-id="b99dc-128">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="b99dc-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="b99dc-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b99dc-129">See also</span></span>

- [<span data-ttu-id="b99dc-130">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b99dc-130">Configuration file schema for the .NET Framework</span></span>](index.md)
