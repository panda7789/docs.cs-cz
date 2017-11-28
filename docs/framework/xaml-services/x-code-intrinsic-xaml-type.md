---
title: "x:Code – vnitřní typ jazyka XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
caps.latest.revision: "19"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: d1b21e2a654b18547c8da7da724c87946724f71f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="8e48b-102">x:Code – vnitřní typ jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="8e48b-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="8e48b-103">Umožňuje, aby umísťování kódu v rámci provozní XAML.</span><span class="sxs-lookup"><span data-stu-id="8e48b-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="8e48b-104">Takový kód můžete buď zkompilují žádnou implementaci procesoru XAML kompilovaný XAML nebo vlevo v produkčním prostředí XAML pro pozdější použití například výklad o modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="8e48b-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="8e48b-105">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="8e48b-105">XAML Object Element Usage</span></span>  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a><span data-ttu-id="8e48b-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8e48b-106">Remarks</span></span>  
 <span data-ttu-id="8e48b-107">Kód v rámci `x:Code` element direktivy jazyka XAML je stále interpretovat v rámci obecné obor názvů XML a obory názvů jazyka XAML zadat.</span><span class="sxs-lookup"><span data-stu-id="8e48b-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="8e48b-108">Proto je obvykle potřeba uzavřete kód použitý pro `x:Code` uvnitř `CDATA` segmentu.</span><span class="sxs-lookup"><span data-stu-id="8e48b-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>  
  
 <span data-ttu-id="8e48b-109">`x:Code`není povoleno pro všechny možné nasazení mechanismy provozních XAML.</span><span class="sxs-lookup"><span data-stu-id="8e48b-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="8e48b-110">V konkrétní rozhraní (například WPF) musí být zkompilovány kód.</span><span class="sxs-lookup"><span data-stu-id="8e48b-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="8e48b-111">V jiných rozhraní `x:Code` využití může obecně zakázán.</span><span class="sxs-lookup"><span data-stu-id="8e48b-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>  
  
 <span data-ttu-id="8e48b-112">Pro rozhraní, které umožňují spravované `x:Code` obsahu, kompilátoru správný jazyk pro `x:Code` obsah je dáno nastavení a cíle obsahující projekt, který se používá ke kompilaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="8e48b-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="8e48b-113">Poznámky pro použití WPF</span><span class="sxs-lookup"><span data-stu-id="8e48b-113">WPF Usage Notes</span></span>  
 <span data-ttu-id="8e48b-114">Kód deklarované v rámci `x:Code` pro WPF má několik upozorňují na důležité omezení:</span><span class="sxs-lookup"><span data-stu-id="8e48b-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>  
  
-   <span data-ttu-id="8e48b-115">`x:Code` – Element direktivy musí být okamžitou podřízený prvek kořenového prvku provozních XAML.</span><span class="sxs-lookup"><span data-stu-id="8e48b-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>  
  
-   <span data-ttu-id="8e48b-116">[x: Class – direktiva](../../../docs/framework/xaml-services/x-class-directive.md) je třeba zadat v kořenovém elementu nadřazené.</span><span class="sxs-lookup"><span data-stu-id="8e48b-116">[x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) must be provided on the parent root element.</span></span>  
  
-   <span data-ttu-id="8e48b-117">Kód umístit `x:Code` nakládáno kompilace musí být v rozsahu částečné třídy, která už se vytváří této stránky XAML.</span><span class="sxs-lookup"><span data-stu-id="8e48b-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="8e48b-118">Proto všechny kódu, které definujete musí být členy nebo proměnné částečné třídy.</span><span class="sxs-lookup"><span data-stu-id="8e48b-118">Therefore all code you define must be members or variables of that partial class.</span></span>  
  
-   <span data-ttu-id="8e48b-119">Nelze definovat další třídy, jiné než pomocí vnoření třídu uvnitř třídu (vnoření je povoleno, ale není typické, že vnořené třídy nelze odkazovat v jazyce XAML).</span><span class="sxs-lookup"><span data-stu-id="8e48b-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="8e48b-120">Obory názvů CLR než obor názvů, který se používá pro existující třídu nelze definované nebo přidat do.</span><span class="sxs-lookup"><span data-stu-id="8e48b-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>  
  
-   <span data-ttu-id="8e48b-121">Odkazy na entity kód mimo obor názvů třídu CLR musí být plně kvalifikovaný.</span><span class="sxs-lookup"><span data-stu-id="8e48b-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="8e48b-122">Členové se deklarovat jsou přepsání přepisovatelné členům třídu, musí zadat pomocí klíčového slova přepsání konkrétní jazyk.</span><span class="sxs-lookup"><span data-stu-id="8e48b-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="8e48b-123">Pokud deklarované členy v `x:Code` oboru v konfliktu s členové třídu vytvořený mimo XAML, tak, že kompilátor sestavy konflikt, souboru XAML nelze zkompilovat nebo zatížení.</span><span class="sxs-lookup"><span data-stu-id="8e48b-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e48b-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e48b-124">See Also</span></span>  
 [<span data-ttu-id="8e48b-125">x: Class – direktiva</span><span class="sxs-lookup"><span data-stu-id="8e48b-125">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="8e48b-126">Kódu a XAML v grafickém subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="8e48b-126">Code-Behind and XAML in WPF</span></span>](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [<span data-ttu-id="8e48b-127">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="8e48b-127">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
