---
title: x:Reference – rozšíření značek
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: 960f5c0e4192df72090c1a571dfc2fc5e3fd8ba3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562242"
---
# <a name="xreference-markup-extension"></a><span data-ttu-id="820ac-102">x:Reference – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="820ac-102">x:Reference Markup Extension</span></span>
<span data-ttu-id="820ac-103">Odkazuje na instanci, která je deklarovaná jinde v XAML značek.</span><span class="sxs-lookup"><span data-stu-id="820ac-103">References an instance that is declared elsewhere in XAML markup.</span></span> <span data-ttu-id="820ac-104">Odkaz na odkazuje na element `x:Name`.</span><span class="sxs-lookup"><span data-stu-id="820ac-104">The reference refers to an element's `x:Name`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="820ac-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="820ac-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Reference instancexName}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="820ac-106">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="820ac-106">XAML Object Element Usage</span></span>  
  
```xaml  
<object>  
  <object.property>  
    <x:Reference Name="instancexName"/>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="820ac-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="820ac-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`instancexName`|<span data-ttu-id="820ac-108">`x:Name` Hodnotu (číslo nebo <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identifikovat vlastnost) odkazované instance.</span><span class="sxs-lookup"><span data-stu-id="820ac-108">The `x:Name` value (or value of the <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identified property) of the referenced instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="820ac-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="820ac-109">Remarks</span></span>  
 <span data-ttu-id="820ac-110">`x:Reference` poskytuje podporu úroveň jazyka XAML pro koncept odkaz na element, které je jinak implementováno v určité rozhraní, jako je například WPF.</span><span class="sxs-lookup"><span data-stu-id="820ac-110">`x:Reference` provides XAML language-level support for an element reference concept that was otherwise implemented in specific frameworks such as WPF.</span></span>  
  
## <a name="xreference-and-wpf"></a><span data-ttu-id="820ac-111">x: Reference a WPF</span><span class="sxs-lookup"><span data-stu-id="820ac-111">x:Reference and WPF</span></span>  
 <span data-ttu-id="820ac-112">WPF a XAML 2006, jsou odkazy na element řešené pomocí funkce úrovni rozhraní <xref:System.Windows.Data.Binding.ElementName%2A> vazby.</span><span class="sxs-lookup"><span data-stu-id="820ac-112">In WPF and XAML 2006, element references are addressed by the framework-level feature of <xref:System.Windows.Data.Binding.ElementName%2A> binding.</span></span> <span data-ttu-id="820ac-113">Pro většinu grafického subsystému WPF aplikace a scénáře <xref:System.Windows.Data.Binding.ElementName%2A> vazba by měla používat.</span><span class="sxs-lookup"><span data-stu-id="820ac-113">For most WPF applications and scenarios, <xref:System.Windows.Data.Binding.ElementName%2A> binding should still be used.</span></span> <span data-ttu-id="820ac-114">Výjimky pro tyto obecné pokyny mohou zahrnovat případech, kde jsou kontextu dat nebo další oboru důležité informace, které datová vazba nepraktické a kde kompilace kódu není zahrnut.</span><span class="sxs-lookup"><span data-stu-id="820ac-114">Exceptions to this general guidance might include cases where there are data context or other scoping considerations that make data binding impractical and where markup compilation is not involved.</span></span>  
  
 <span data-ttu-id="820ac-115">`x:Reference` je konstrukt definován v jazyce XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="820ac-115">`x:Reference` is a construct defined in XAML 2009.</span></span> <span data-ttu-id="820ac-116">V grafickém subsystému WPF můžete použít funkce jazyka XAML 2009, ale jenom pro jazyk XAML, který není WPF zkompilovat kód.</span><span class="sxs-lookup"><span data-stu-id="820ac-116">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="820ac-117">Zkompilovaný kód XAML a BAML formu XAML aktuálně nepodporují klíčová slova jazyka XAML 2009 a funkce.</span><span class="sxs-lookup"><span data-stu-id="820ac-117">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>
