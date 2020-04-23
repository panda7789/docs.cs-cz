---
title: x:Reference – rozšíření značek
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: f06e259893111a436e5afe2df754c3edee326d54
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071379"
---
# <a name="xreference-markup-extension"></a><span data-ttu-id="89b10-102">x:Reference – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="89b10-102">x:Reference Markup Extension</span></span>

<span data-ttu-id="89b10-103">Odkazuje na instanci, která je deklarována jinde ve značkách XAML.</span><span class="sxs-lookup"><span data-stu-id="89b10-103">References an instance that is declared elsewhere in XAML markup.</span></span> <span data-ttu-id="89b10-104">Odkaz odkazuje na prvek `x:Name`.</span><span class="sxs-lookup"><span data-stu-id="89b10-104">The reference refers to an element's `x:Name`.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="89b10-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="89b10-105">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Reference instancexName}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="89b10-106">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="89b10-106">XAML Object Element Usage</span></span>

```xaml
<object>
  <object.property>
    <x:Reference Name="instancexName"/>
  </object.property>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="89b10-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="89b10-107">XAML Values</span></span>

|||
|-|-|
|`instancexName`|<span data-ttu-id="89b10-108">Hodnota `x:Name` (nebo hodnota <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identified vlastnost) odkazované instance.</span><span class="sxs-lookup"><span data-stu-id="89b10-108">The `x:Name` value (or value of the <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identified property) of the referenced instance.</span></span>|

## <a name="remarks"></a><span data-ttu-id="89b10-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89b10-109">Remarks</span></span>

<span data-ttu-id="89b10-110">`x:Reference`poskytuje podporu na jazykové úrovni XAML pro koncept odkazu na prvek, který byl jinak implementován v konkrétních architekturách, jako je WPF.</span><span class="sxs-lookup"><span data-stu-id="89b10-110">`x:Reference` provides XAML language-level support for an element reference concept that was otherwise implemented in specific frameworks such as WPF.</span></span>

## <a name="xreference-and-wpf"></a><span data-ttu-id="89b10-111">x:Reference a WPF</span><span class="sxs-lookup"><span data-stu-id="89b10-111">x:Reference and WPF</span></span>

<span data-ttu-id="89b10-112">V WPF a XAML 2006 jsou odkazy na element y <xref:System.Windows.Data.Binding.ElementName%2A> adresovány funkcí vazby na úrovni rozhraní.</span><span class="sxs-lookup"><span data-stu-id="89b10-112">In WPF and XAML 2006, element references are addressed by the framework-level feature of <xref:System.Windows.Data.Binding.ElementName%2A> binding.</span></span> <span data-ttu-id="89b10-113">Pro většinu wpf aplikací <xref:System.Windows.Data.Binding.ElementName%2A> a scénářů by měla být stále použita vazba.</span><span class="sxs-lookup"><span data-stu-id="89b10-113">For most WPF applications and scenarios, <xref:System.Windows.Data.Binding.ElementName%2A> binding should still be used.</span></span> <span data-ttu-id="89b10-114">Výjimky z těchto obecných pokynů mohou zahrnovat případy, kdy existují kontext dat nebo jiné aspekty oboru, které činí vazbu dat nepraktickou a kde se nejedná o kompilaci značek.</span><span class="sxs-lookup"><span data-stu-id="89b10-114">Exceptions to this general guidance might include cases where there are data context or other scoping considerations that make data binding impractical and where markup compilation is not involved.</span></span>

<span data-ttu-id="89b10-115">`x:Reference`je konstrukce definovaná v XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="89b10-115">`x:Reference` is a construct defined in XAML 2009.</span></span> <span data-ttu-id="89b10-116">V WPF můžete použít funkce XAML 2009, ale pouze pro XAML, který není wpf zkompilovaný značky.</span><span class="sxs-lookup"><span data-stu-id="89b10-116">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="89b10-117">KódXAML zkompilovaný značkami a forma XAML BAML aktuálně nepodporují klíčová slova a funkce jazyka XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="89b10-117">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>
