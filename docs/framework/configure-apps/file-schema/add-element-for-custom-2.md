---
title: <add>– element pro NameValueSectionHandler a DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
ms.openlocfilehash: 57722f3518fad12cb8e6e35d68f40bb8465bdd86
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215438"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="39710-102">\<add>– element pro NameValueSectionHandler a DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="39710-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="39710-103">Přidá vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="39710-103">Adds custom application settings.</span></span> <span data-ttu-id="39710-104">Každá **\<add>** značka obsahuje dvojici klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="39710-104">Each **\<add>** tag contains a key/value pair.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="39710-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39710-105">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="39710-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="39710-106">Attributes</span></span>

| <span data-ttu-id="39710-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="39710-107">Attribute</span></span> | <span data-ttu-id="39710-108">Popis</span><span class="sxs-lookup"><span data-stu-id="39710-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="39710-109">**zkrat**</span><span class="sxs-lookup"><span data-stu-id="39710-109">**key**</span></span>   | <span data-ttu-id="39710-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="39710-110">Required attribute.</span></span><br><br><span data-ttu-id="39710-111">Určuje název nastavení.</span><span class="sxs-lookup"><span data-stu-id="39710-111">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="39710-112">**osa**</span><span class="sxs-lookup"><span data-stu-id="39710-112">**value**</span></span> | <span data-ttu-id="39710-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="39710-113">Required attribute.</span></span><br><br><span data-ttu-id="39710-114">Určuje hodnotu nastavení.</span><span class="sxs-lookup"><span data-stu-id="39710-114">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="39710-115">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="39710-115">Parent element</span></span>

| <span data-ttu-id="39710-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="39710-116">Element</span></span> | <span data-ttu-id="39710-117">Description</span><span class="sxs-lookup"><span data-stu-id="39710-117">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="39710-118">**\<sectionName>** Objekt</span><span class="sxs-lookup"><span data-stu-id="39710-118">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="39710-119">Definuje nastavení pro vlastní konfigurační oddíly, které používají <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> třídy a.</span><span class="sxs-lookup"><span data-stu-id="39710-119">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="39710-120">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="39710-120">Child elements</span></span>

<span data-ttu-id="39710-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="39710-121">None</span></span>

## <a name="example"></a><span data-ttu-id="39710-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="39710-122">Example</span></span>

<span data-ttu-id="39710-123">Následující příklad ukazuje, jak definovat vlastní konfigurační oddíl a použít **\<add>** element k umístění nastavení do oddílu:</span><span class="sxs-lookup"><span data-stu-id="39710-123">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="39710-124">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="39710-124">Configuration file</span></span>

<span data-ttu-id="39710-125">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="39710-125">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="39710-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="39710-126">See also</span></span>

- [<span data-ttu-id="39710-127">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="39710-127">Configuration file schema for the .NET Framework</span></span>](index.md)
