---
title: Vlastní element pro NameValueSectionHandler a DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d73c07d58bb226346cb99a1fe50b12bb0e7e746e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118533"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="06caf-102">Vlastní element pro NameValueSectionHandler a DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="06caf-102">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="06caf-103">Definuje nastavení pro vlastní konfigurační oddíly, které používají třídy <xref:System.Configuration.NameValueSectionHandler> a <xref:System.Configuration.DictionarySectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="06caf-103">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

<span data-ttu-id="06caf-104">[ **\<configuration >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="06caf-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="06caf-105">&nbsp;&nbsp; **\<sectiongroup >**</span><span class="sxs-lookup"><span data-stu-id="06caf-105">&nbsp;&nbsp;**\<sectionName>**</span></span>

## <a name="attributes"></a><span data-ttu-id="06caf-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="06caf-106">Attributes</span></span>

<span data-ttu-id="06caf-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="06caf-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="06caf-108">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="06caf-108">Parent element</span></span>

|     | <span data-ttu-id="06caf-109">Popis</span><span class="sxs-lookup"><span data-stu-id="06caf-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="06caf-110">**Konfigurace \<** </span><span class="sxs-lookup"><span data-stu-id="06caf-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="06caf-111">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="06caf-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="06caf-112">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="06caf-112">Child elements</span></span>

|     | <span data-ttu-id="06caf-113">Popis</span><span class="sxs-lookup"><span data-stu-id="06caf-113">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="06caf-114">[ **\<přidat >** ](add-element-for-custom-2.md) pro <xref:System.Configuration.NameValueSectionHandler> a <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="06caf-114">[**\<add>**](add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="06caf-115">Přidá vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="06caf-115">Adds custom application settings.</span></span> |
| <span data-ttu-id="06caf-116">[ **\<odebrat >** ](remove-element-for-custom-2.md) pro <xref:System.Configuration.NameValueSectionHandler> a <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="06caf-116">[**\<remove>**](remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="06caf-117">Odebere dříve definované nastavení.</span><span class="sxs-lookup"><span data-stu-id="06caf-117">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="06caf-118">[ **\<vymazat >** ](clear-element-for-custom-2.md) pro <xref:System.Configuration.NameValueSectionHandler> a <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="06caf-118">[**\<clear>**](clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="06caf-119">Vymaže všechna dříve definovaná nastavení v oddílu.</span><span class="sxs-lookup"><span data-stu-id="06caf-119">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="06caf-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="06caf-120">Remarks</span></span>

<span data-ttu-id="06caf-121">Element **\<** je vlastní element definovaný **\<oddílem >** značky v\<m prvku **> configSections** .</span><span class="sxs-lookup"><span data-stu-id="06caf-121">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="06caf-122">V následující tabulce je uveden typ objektu, který metoda ConfigurationSettings. GetConfig vrátí pro každou obslužnou rutinu konfiguračního oddílu:</span><span class="sxs-lookup"><span data-stu-id="06caf-122">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="06caf-123">Obslužná rutina konfiguračního oddílu</span><span class="sxs-lookup"><span data-stu-id="06caf-123">Configuration section handler</span></span>                        | <span data-ttu-id="06caf-124">Návratový typ</span><span class="sxs-lookup"><span data-stu-id="06caf-124">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="06caf-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="06caf-125">Example</span></span>

<span data-ttu-id="06caf-126">Následující příklad ukazuje, jak deklarovat oddíly, které používají <xref:System.Configuration.DictionarySectionHandler> a <xref:System.Configuration.NameValueSectionHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="06caf-126">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span>

<span data-ttu-id="06caf-127">Prvním vlastním prvkem je **\<dictionarySample >** , který obsahuje nastavení čtená třídou <xref:System.Configuration.DictionarySectionHandler> v sestavení `System.dll`.</span><span class="sxs-lookup"><span data-stu-id="06caf-127">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="06caf-128">Druhý vlastní prvek je **\<mySection >** , který obsahuje nastavení čtená třídou <xref:System.Configuration.NameValueSectionHandler> v sestavení `System.dll`.</span><span class="sxs-lookup"><span data-stu-id="06caf-128">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
    <sectionGroup name="mySectionGroup">
      <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="06caf-129">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="06caf-129">Configuration file</span></span>

<span data-ttu-id="06caf-130">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="06caf-130">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="06caf-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06caf-131">See also</span></span>

- [<span data-ttu-id="06caf-132">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="06caf-132">Configuration file schema for the .NET Framework</span></span>](index.md)
