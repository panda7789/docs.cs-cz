---
title: <remove>– element pro NameValueSectionHandler a DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
ms.openlocfilehash: d1e4f3478f6afd6a20c01c6b57a137020ee88f5f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214758"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="669ae-102">\<remove>– element pro NameValueSectionHandler a DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="669ae-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="669ae-103">Odebere dříve definované nastavení.</span><span class="sxs-lookup"><span data-stu-id="669ae-103">Removes a previously defined setting.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="669ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="669ae-104">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="669ae-105">Atribut</span><span class="sxs-lookup"><span data-stu-id="669ae-105">Attribute</span></span>

|           | <span data-ttu-id="669ae-106">Popis</span><span class="sxs-lookup"><span data-stu-id="669ae-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="669ae-107">**zkrat**</span><span class="sxs-lookup"><span data-stu-id="669ae-107">**key**</span></span>   | <span data-ttu-id="669ae-108">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="669ae-108">Required attribute.</span></span><br><br><span data-ttu-id="669ae-109">Určuje název nastavení, které se má odebrat.</span><span class="sxs-lookup"><span data-stu-id="669ae-109">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="669ae-110">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="669ae-110">Parent element</span></span>

| <span data-ttu-id="669ae-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="669ae-111">Element</span></span> | <span data-ttu-id="669ae-112">Description</span><span class="sxs-lookup"><span data-stu-id="669ae-112">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="669ae-113">**\<sectionName>** Objekt</span><span class="sxs-lookup"><span data-stu-id="669ae-113">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="669ae-114">Definuje nastavení pro vlastní konfigurační oddíly, které používají <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> třídy a.</span><span class="sxs-lookup"><span data-stu-id="669ae-114">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="669ae-115">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="669ae-115">Child elements</span></span>

<span data-ttu-id="669ae-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="669ae-116">None</span></span>

## <a name="remarks"></a><span data-ttu-id="669ae-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="669ae-117">Remarks</span></span>

<span data-ttu-id="669ae-118">Pomocí **\<remove>** elementu můžete odebrat nastavení z aplikace, které bylo definováno na vyšší úrovni v hierarchii konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="669ae-118">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="669ae-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="669ae-119">Example</span></span>

<span data-ttu-id="669ae-120">Následující příklad ukazuje, jak použít **\<remove>** element v konfiguračním souboru aplikace k odebrání nastavení dříve definovaného v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="669ae-120">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="669ae-121">Následující kód konfiguračního souboru počítače deklaruje oddíl **\<mySection>** a přidá dvě nastavení `key1` a `key2` do něj:</span><span class="sxs-lookup"><span data-stu-id="669ae-121">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

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

<span data-ttu-id="669ae-122">Následující kód konfiguračního souboru aplikace odebere `key2` nastavení z **\<mySection>** :</span><span class="sxs-lookup"><span data-stu-id="669ae-122">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="669ae-123">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="669ae-123">Configuration file</span></span>

<span data-ttu-id="669ae-124">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="669ae-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="669ae-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="669ae-125">See also</span></span>

- [<span data-ttu-id="669ae-126">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="669ae-126">Configuration file schema for the .NET Framework</span></span>](index.md)
