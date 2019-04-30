---
title: x:Reference – rozšíření značek
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: 960f5c0e4192df72090c1a571dfc2fc5e3fd8ba3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938876"
---
# <a name="xreference-markup-extension"></a><span data-ttu-id="06d26-102">x:Reference – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="06d26-102">x:Reference Markup Extension</span></span>
<span data-ttu-id="06d26-103">Odkazuje na instanci, která je někde jinde deklarovaný ve značkách XAML.</span><span class="sxs-lookup"><span data-stu-id="06d26-103">References an instance that is declared elsewhere in XAML markup.</span></span> <span data-ttu-id="06d26-104">Odkaz na odkazuje na element `x:Name`.</span><span class="sxs-lookup"><span data-stu-id="06d26-104">The reference refers to an element's `x:Name`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="06d26-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="06d26-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Reference instancexName}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="06d26-106">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="06d26-106">XAML Object Element Usage</span></span>  
  
```xaml  
<object>  
  <object.property>  
    <x:Reference Name="instancexName"/>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="06d26-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="06d26-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`instancexName`|<span data-ttu-id="06d26-108">`x:Name` Hodnotu (nebo hodnota <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identifikované vlastnosti) odkazované instance.</span><span class="sxs-lookup"><span data-stu-id="06d26-108">The `x:Name` value (or value of the <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identified property) of the referenced instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06d26-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="06d26-109">Remarks</span></span>  
 <span data-ttu-id="06d26-110">`x:Reference` poskytuje podporu na úrovni jazyka XAML pro pojem referenční dokumentace elementu, jinak implementovaný v konkrétní architektury, jako jsou WPF.</span><span class="sxs-lookup"><span data-stu-id="06d26-110">`x:Reference` provides XAML language-level support for an element reference concept that was otherwise implemented in specific frameworks such as WPF.</span></span>  
  
## <a name="xreference-and-wpf"></a><span data-ttu-id="06d26-111">x: Reference a WPF</span><span class="sxs-lookup"><span data-stu-id="06d26-111">x:Reference and WPF</span></span>  
 <span data-ttu-id="06d26-112">V XAML 2006 a WPF, odkazy na prvky se tak vyřeší, funkce úrovni architektury <xref:System.Windows.Data.Binding.ElementName%2A> vazby.</span><span class="sxs-lookup"><span data-stu-id="06d26-112">In WPF and XAML 2006, element references are addressed by the framework-level feature of <xref:System.Windows.Data.Binding.ElementName%2A> binding.</span></span> <span data-ttu-id="06d26-113">Pro většinu aplikací WPF a scénáře <xref:System.Windows.Data.Binding.ElementName%2A> vazba by měla i nadále sloužit.</span><span class="sxs-lookup"><span data-stu-id="06d26-113">For most WPF applications and scenarios, <xref:System.Windows.Data.Binding.ElementName%2A> binding should still be used.</span></span> <span data-ttu-id="06d26-114">Výjimky z této obecné pokyny mohou zahrnovat případy, kde jsou kontext dat nebo jiných oborů aspekty, které usnadňují vytváření datových vazeb nepraktické a není součástí kompilace označení.</span><span class="sxs-lookup"><span data-stu-id="06d26-114">Exceptions to this general guidance might include cases where there are data context or other scoping considerations that make data binding impractical and where markup compilation is not involved.</span></span>  
  
 <span data-ttu-id="06d26-115">`x:Reference` použít konstrukce definované v XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="06d26-115">`x:Reference` is a construct defined in XAML 2009.</span></span> <span data-ttu-id="06d26-116">V WPF můžete použít funkce XAML 2009, ale pouze pro XAML, který není kompilována značka WPF.</span><span class="sxs-lookup"><span data-stu-id="06d26-116">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="06d26-117">Kompilována značka XAML a formulář BAML z XAML aktuálně nepodporují klíčová slova jazyka XAML 2009 a funkce.</span><span class="sxs-lookup"><span data-stu-id="06d26-117">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>
