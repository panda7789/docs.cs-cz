---
title: Vlastní element pro NameValueSectionHandler a DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 890269857aaa00ce62195ccb2f4cb184b363b61e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921020"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="3bfed-102">Vlastní element pro NameValueSectionHandler a DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="3bfed-102">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="3bfed-103">Definuje nastavení pro vlastní konfigurační oddíly, které používají <xref:System.Configuration.NameValueSectionHandler> třídy <xref:System.Configuration.DictionarySectionHandler> a.</span><span class="sxs-lookup"><span data-stu-id="3bfed-103">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

<span data-ttu-id="3bfed-104">[ **\<> Konfigurace**](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3bfed-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="3bfed-105">&nbsp;&nbsp; **\<sectionName>**</span><span class="sxs-lookup"><span data-stu-id="3bfed-105">&nbsp;&nbsp;**\<sectionName>**</span></span>

## <a name="attributes"></a><span data-ttu-id="3bfed-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="3bfed-106">Attributes</span></span>

<span data-ttu-id="3bfed-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="3bfed-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="3bfed-108">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="3bfed-108">Parent element</span></span>

|     | <span data-ttu-id="3bfed-109">Popis</span><span class="sxs-lookup"><span data-stu-id="3bfed-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3bfed-110"> **\<> Konfigurace**</span><span class="sxs-lookup"><span data-stu-id="3bfed-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="3bfed-111">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3bfed-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="3bfed-112">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="3bfed-112">Child elements</span></span>

|     | <span data-ttu-id="3bfed-113">Popis</span><span class="sxs-lookup"><span data-stu-id="3bfed-113">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="3bfed-114">Přidání > pro a [ **\<** ](add-element-for-custom-2.md) <xref:System.Configuration.NameValueSectionHandler><xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="3bfed-114">[**\<add>**](add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="3bfed-115">Přidá vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="3bfed-115">Adds custom application settings.</span></span> |
| <span data-ttu-id="3bfed-116">odebrat > pro a [ **\<** ](remove-element-for-custom-2.md) <xref:System.Configuration.NameValueSectionHandler><xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="3bfed-116">[**\<remove>**](remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="3bfed-117">Odebere dříve definované nastavení.</span><span class="sxs-lookup"><span data-stu-id="3bfed-117">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="3bfed-118">Vymazat > pro a [ **\<** ](clear-element-for-custom-2.md) <xref:System.Configuration.NameValueSectionHandler><xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="3bfed-118">[**\<clear>**](clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="3bfed-119">Vymaže všechna dříve definovaná nastavení v oddílu.</span><span class="sxs-lookup"><span data-stu-id="3bfed-119">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="3bfed-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3bfed-120">Remarks</span></span>

<span data-ttu-id="3bfed-121">**\<SectionName>** prvek je prvek vlastní, určené **\<části>** značku **\<configSections>** elementu.</span><span class="sxs-lookup"><span data-stu-id="3bfed-121">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="3bfed-122">V následující tabulce je uveden typ objektu, který metoda ConfigurationSettings. GetConfig vrátí pro každou obslužnou rutinu konfiguračního oddílu:</span><span class="sxs-lookup"><span data-stu-id="3bfed-122">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="3bfed-123">Obslužná rutina konfiguračního oddílu</span><span class="sxs-lookup"><span data-stu-id="3bfed-123">Configuration section handler</span></span>                        | <span data-ttu-id="3bfed-124">Návratový typ</span><span class="sxs-lookup"><span data-stu-id="3bfed-124">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="3bfed-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="3bfed-125">Example</span></span>

<span data-ttu-id="3bfed-126">Následující příklad ukazuje, jak deklarovat oddíly, které používají <xref:System.Configuration.DictionarySectionHandler> třídy a. <xref:System.Configuration.NameValueSectionHandler></span><span class="sxs-lookup"><span data-stu-id="3bfed-126">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span>

<span data-ttu-id="3bfed-127">Prvním vlastním prvkem je  **\<dictionarySample >** , který obsahuje <xref:System.Configuration.DictionarySectionHandler> nastavení čtená třídou v `System.dll` sestavení.</span><span class="sxs-lookup"><span data-stu-id="3bfed-127">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="3bfed-128">Druhý vlastní prvek je  **\<mySection >** , který obsahuje <xref:System.Configuration.NameValueSectionHandler> nastavení čtená třídou v `System.dll` sestavení.</span><span class="sxs-lookup"><span data-stu-id="3bfed-128">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="3bfed-129">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="3bfed-129">Configuration file</span></span>

<span data-ttu-id="3bfed-130">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="3bfed-130">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="3bfed-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3bfed-131">See also</span></span>

- [<span data-ttu-id="3bfed-132">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3bfed-132">Configuration file schema for the .NET Framework</span></span>](index.md)
