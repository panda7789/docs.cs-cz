---
title: x:Code – vnitřní typ jazyka XAML
ms.date: 03/30/2017
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
ms.openlocfilehash: 7312c59cdcddfdbda39a4a9f05788b6a021f9b75
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459587"
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="fa7da-102">x:Code – vnitřní typ jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="fa7da-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="fa7da-103">Umožňuje umístění kódu v rámci výroby XAML.</span><span class="sxs-lookup"><span data-stu-id="fa7da-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="fa7da-104">Takový kód může být zkompilován v jakékoli implementaci procesoru XAML, která kompiluje XAML nebo ponechána v produkci XAML pro pozdější použití, jako je například interpretace modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="fa7da-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="fa7da-105">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="fa7da-105">XAML Object Element Usage</span></span>  
  
```xaml  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a><span data-ttu-id="fa7da-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fa7da-106">Remarks</span></span>  
 <span data-ttu-id="fa7da-107">Kód v rámci elementu direktivy `x:Code` XAML je stále interpretován v rámci obecného oboru názvů XML a poskytnuté obory názvů XAML.</span><span class="sxs-lookup"><span data-stu-id="fa7da-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="fa7da-108">Proto je obvykle nutné uzavřít kód, který se používá pro `x:Code` uvnitř segmentu `CDATA`.</span><span class="sxs-lookup"><span data-stu-id="fa7da-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>  
  
 <span data-ttu-id="fa7da-109">`x:Code` není povolený pro všechny možné mechanismy nasazení v produkci XAML.</span><span class="sxs-lookup"><span data-stu-id="fa7da-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="fa7da-110">V konkrétních rozhraních (například WPF) musí být kód zkompilován.</span><span class="sxs-lookup"><span data-stu-id="fa7da-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="fa7da-111">V jiných rozhraních může být použití `x:Code` obecně zakázáno.</span><span class="sxs-lookup"><span data-stu-id="fa7da-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>  
  
 <span data-ttu-id="fa7da-112">Pro architektury, které povolují spravovaný obsah `x:Code`, je správný kompilátor jazyka, který se má použít pro `x:Code` obsah, určen nastavením a cíli obsahujícího projektu, který se používá ke kompilaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="fa7da-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="fa7da-113">Poznámky k použití WPF</span><span class="sxs-lookup"><span data-stu-id="fa7da-113">WPF Usage Notes</span></span>  
 <span data-ttu-id="fa7da-114">Kód deklarovaný v rámci `x:Code` pro WPF má několik důležitých omezení:</span><span class="sxs-lookup"><span data-stu-id="fa7da-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>  
  
- <span data-ttu-id="fa7da-115">Element direktivy `x:Code` musí být bezprostředním podřízeným elementem kořenového elementu v produkci XAML.</span><span class="sxs-lookup"><span data-stu-id="fa7da-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>  
  
- <span data-ttu-id="fa7da-116">v nadřazeném kořenovém elementu musí být zadána [direktiva x:Class](x-class-directive.md) .</span><span class="sxs-lookup"><span data-stu-id="fa7da-116">[x:Class Directive](x-class-directive.md) must be provided on the parent root element.</span></span>  
  
- <span data-ttu-id="fa7da-117">Kód umístěný v rámci `x:Code` bude zpracován kompilací, aby byl v rámci oboru částečné třídy, která je již vytvořena pro tuto stránku XAML.</span><span class="sxs-lookup"><span data-stu-id="fa7da-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="fa7da-118">Proto všechen kód, který definujete, musí být členy nebo proměnné této dílčí třídy.</span><span class="sxs-lookup"><span data-stu-id="fa7da-118">Therefore all code you define must be members or variables of that partial class.</span></span>  
  
- <span data-ttu-id="fa7da-119">Nelze definovat další třídy, jiné než vnořování třídy uvnitř dílčí třídy (vnořování je povoleno, ale není to obvyklé, protože vnořené třídy nemohou být v jazyce XAML odkazovány).</span><span class="sxs-lookup"><span data-stu-id="fa7da-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="fa7da-120">Obory názvů CLR jiné než obor názvů, který se používá pro existující částečnou třídu, nelze definovat ani přidat do.</span><span class="sxs-lookup"><span data-stu-id="fa7da-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>  
  
- <span data-ttu-id="fa7da-121">Odkazy na entity kódu mimo obor názvů částečného CLR třídy musí být plně kvalifikované.</span><span class="sxs-lookup"><span data-stu-id="fa7da-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="fa7da-122">Pokud jsou členové deklarováni, je nutné zadat klíčové slovo override pro částečnou třídu.</span><span class="sxs-lookup"><span data-stu-id="fa7da-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="fa7da-123">Jsou-li členové deklarované v `x:Code` rozsahu v konfliktu se členy částečné třídy vytvořenými z jazyka XAML, takovým způsobem, který kompilátor ohlásí konflikt, nemůže soubor XAML kompilovat nebo načíst.</span><span class="sxs-lookup"><span data-stu-id="fa7da-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa7da-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa7da-124">See also</span></span>

- [<span data-ttu-id="fa7da-125">x:Class – direktiva</span><span class="sxs-lookup"><span data-stu-id="fa7da-125">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="fa7da-126">Podkladový kód a kód XAML v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="fa7da-126">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="fa7da-127">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="fa7da-127">XAML Overview (WPF)</span></span>](../../desktop-wpf/fundamentals/xaml.md)
