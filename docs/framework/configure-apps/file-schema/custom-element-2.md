---
title: "Vlastní element NameValueSectionHandler a DictionarySectionHandler"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2154e2a178050e5bafa7d19f37a766141d0a5838
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="7b698-102">Vlastní element NameValueSectionHandler a DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="7b698-102">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="7b698-103">Definuje nastavení pro vlastní konfiguračních oddílů, které používají <xref:System.Configuration.NameValueSectionHandler> a <xref:System.Configuration.DictionarySectionHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="7b698-103">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

<span data-ttu-id="7b698-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="7b698-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="7b698-105">&nbsp;&nbsp;**\<sectionName >**</span><span class="sxs-lookup"><span data-stu-id="7b698-105">&nbsp;&nbsp;**\<sectionName>**</span></span>

## <a name="attributes"></a><span data-ttu-id="7b698-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="7b698-106">Attributes</span></span>

<span data-ttu-id="7b698-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="7b698-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="7b698-108">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="7b698-108">Parent element</span></span>

|     | <span data-ttu-id="7b698-109">Popis</span><span class="sxs-lookup"><span data-stu-id="7b698-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="7b698-110">**\<Konfigurace >**</span><span class="sxs-lookup"><span data-stu-id="7b698-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="7b698-111">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b698-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="7b698-112">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="7b698-112">Child elements</span></span>

|     | <span data-ttu-id="7b698-113">Popis</span><span class="sxs-lookup"><span data-stu-id="7b698-113">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="7b698-114">[**\<Přidat >** ](~/docs/framework/configure-apps/file-schema/add-element-for-custom-2.md) pro <xref:System.Configuration.NameValueSectionHandler> a<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="7b698-114">[**\<add>**](~/docs/framework/configure-apps/file-schema/add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="7b698-115">Přidá nastavení vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b698-115">Adds custom application settings.</span></span> |
| <span data-ttu-id="7b698-116">[**\<Odebrat >** ](~/docs/framework/configure-apps/file-schema/remove-element-for-custom-2.md) pro <xref:System.Configuration.NameValueSectionHandler> a<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="7b698-116">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> |    <span data-ttu-id="7b698-117">Odebere dříve definovaném nastavení.</span><span class="sxs-lookup"><span data-stu-id="7b698-117">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="7b698-118">[**\<Clear >** ](~/docs/framework/configure-apps/file-schema/clear-element-for-custom-2.md) pro <xref:System.Configuration.NameValueSectionHandler> a<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="7b698-118">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="7b698-119">Vymaže všechny dříve definované nastavení v oddílu.</span><span class="sxs-lookup"><span data-stu-id="7b698-119">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="7b698-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b698-120">Remarks</span></span>

<span data-ttu-id="7b698-121"> **\<SectionName >** element je vlastní definované  **\<části >** značky v  **\<configSections >**elementu.</span><span class="sxs-lookup"><span data-stu-id="7b698-121">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="7b698-122">Následující tabulka uvádí, že typ objektu ConfigurationSettings.GetConfig metoda vrátí pro každou obslužnou rutinu konfiguračního oddílu:</span><span class="sxs-lookup"><span data-stu-id="7b698-122">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="7b698-123">Obslužná rutina konfiguračního oddílu</span><span class="sxs-lookup"><span data-stu-id="7b698-123">Configuration section handler</span></span>                        | <span data-ttu-id="7b698-124">Návratový typ</span><span class="sxs-lookup"><span data-stu-id="7b698-124">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="7b698-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b698-125">Example</span></span>

<span data-ttu-id="7b698-126">Následující příklad ukazuje, jak deklarovat oddíly, které chcete použít <xref:System.Configuration.DictionarySectionHandler> a <xref:System.Configuration.NameValueSectionHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="7b698-126">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span> 

<span data-ttu-id="7b698-127">První vlastní element je  **\<dictionarySample >**, který obsahuje nastavení číst <xref:System.Configuration.DictionarySectionHandler> třídy v `System.dll` sestavení.</span><span class="sxs-lookup"><span data-stu-id="7b698-127">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="7b698-128">Druhý vlastní element je  **\<mySection >**, který obsahuje nastavení číst <xref:System.Configuration.NameValueSectionHandler> třídy v `System.dll` sestavení.</span><span class="sxs-lookup"><span data-stu-id="7b698-128">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="7b698-129">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="7b698-129">Configuration file</span></span>

<span data-ttu-id="7b698-130">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b698-130">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b698-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b698-131">See also</span></span>

[<span data-ttu-id="7b698-132">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7b698-132">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
