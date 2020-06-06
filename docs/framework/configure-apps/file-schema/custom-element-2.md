---
title: Vlastní element pro NameValueSectionHandler a DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
ms.openlocfilehash: e5c5c6cf5744aa385e6f6700cad623751a4d7427
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215481"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="8a895-102">Vlastní element pro NameValueSectionHandler a DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="8a895-102">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="8a895-103">Definuje nastavení pro vlastní konfigurační oddíly, které používají <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> třídy a.</span><span class="sxs-lookup"><span data-stu-id="8a895-103">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;**\<sectionName>**

## <a name="attributes"></a><span data-ttu-id="8a895-104">Atributy</span><span class="sxs-lookup"><span data-stu-id="8a895-104">Attributes</span></span>

<span data-ttu-id="8a895-105">Žádné</span><span class="sxs-lookup"><span data-stu-id="8a895-105">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="8a895-106">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="8a895-106">Parent element</span></span>

|     | <span data-ttu-id="8a895-107">Description</span><span class="sxs-lookup"><span data-stu-id="8a895-107">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="8a895-108">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8a895-108">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="8a895-109">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="8a895-109">Child elements</span></span>

|     | <span data-ttu-id="8a895-110">Description</span><span class="sxs-lookup"><span data-stu-id="8a895-110">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="8a895-111">[**\<add>**](add-element-for-custom-2.md)pro <xref:System.Configuration.NameValueSectionHandler> a<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="8a895-111">[**\<add>**](add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="8a895-112">Přidá vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="8a895-112">Adds custom application settings.</span></span> |
| <span data-ttu-id="8a895-113">[**\<remove>**](remove-element-for-custom-2.md)pro <xref:System.Configuration.NameValueSectionHandler> a<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="8a895-113">[**\<remove>**](remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="8a895-114">Odebere dříve definované nastavení.</span><span class="sxs-lookup"><span data-stu-id="8a895-114">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="8a895-115">[**\<clear>**](clear-element-for-custom-2.md)pro <xref:System.Configuration.NameValueSectionHandler> a<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="8a895-115">[**\<clear>**](clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="8a895-116">Vymaže všechna dříve definovaná nastavení v oddílu.</span><span class="sxs-lookup"><span data-stu-id="8a895-116">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="8a895-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8a895-117">Remarks</span></span>

<span data-ttu-id="8a895-118">**\<sectionName>** Element je vlastní element definovaný **\<section>** tagem v **\<configSections>** elementu.</span><span class="sxs-lookup"><span data-stu-id="8a895-118">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="8a895-119">V následující tabulce je uveden typ objektu, který metoda ConfigurationSettings. GetConfig vrátí pro každou obslužnou rutinu konfiguračního oddílu:</span><span class="sxs-lookup"><span data-stu-id="8a895-119">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="8a895-120">Obslužná rutina konfiguračního oddílu</span><span class="sxs-lookup"><span data-stu-id="8a895-120">Configuration section handler</span></span>                        | <span data-ttu-id="8a895-121">Návratový typ</span><span class="sxs-lookup"><span data-stu-id="8a895-121">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="8a895-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="8a895-122">Example</span></span>

<span data-ttu-id="8a895-123">Následující příklad ukazuje, jak deklarovat oddíly, které používají <xref:System.Configuration.DictionarySectionHandler> třídy a <xref:System.Configuration.NameValueSectionHandler> .</span><span class="sxs-lookup"><span data-stu-id="8a895-123">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span>

<span data-ttu-id="8a895-124">První vlastní prvek je **\<dictionarySample>** , který obsahuje nastavení čtená <xref:System.Configuration.DictionarySectionHandler> třídou v `System.dll` sestavení.</span><span class="sxs-lookup"><span data-stu-id="8a895-124">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="8a895-125">Druhý vlastní prvek je **\<mySection>** , který obsahuje nastavení čtená <xref:System.Configuration.NameValueSectionHandler> třídou v `System.dll` sestavení.</span><span class="sxs-lookup"><span data-stu-id="8a895-125">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="8a895-126">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="8a895-126">Configuration file</span></span>

<span data-ttu-id="8a895-127">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="8a895-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a895-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="8a895-128">See also</span></span>

- [<span data-ttu-id="8a895-129">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8a895-129">Configuration file schema for the .NET Framework</span></span>](index.md)
