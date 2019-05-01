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
ms.openlocfilehash: 7bb78b05be7b3edc4471bc276010eabd92a07a14
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971844"
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="cb94c-102">x:Code – vnitřní typ jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="cb94c-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="cb94c-103">Umožňuje umístění kódu v rámci výrobní XAML.</span><span class="sxs-lookup"><span data-stu-id="cb94c-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="cb94c-104">Takový kód můžete buď zkompilován s žádnou implementaci procesoru XAML, který zkompiluje XAML nebo doleva v produkčním prostředí XAML pro pozdější použití například interpretace modulem runtime, který.</span><span class="sxs-lookup"><span data-stu-id="cb94c-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="cb94c-105">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="cb94c-105">XAML Object Element Usage</span></span>  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a><span data-ttu-id="cb94c-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb94c-106">Remarks</span></span>  
 <span data-ttu-id="cb94c-107">Kód v rámci `x:Code` – element direktivy XAML je stále interpretovány v rámci obecné oboru názvů XML a obory názvů XAML k dispozici.</span><span class="sxs-lookup"><span data-stu-id="cb94c-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="cb94c-108">Proto je obvykle nutné uvést kód používá pro `x:Code` uvnitř `CDATA` segmentu.</span><span class="sxs-lookup"><span data-stu-id="cb94c-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>  
  
 <span data-ttu-id="cb94c-109">`x:Code` pro všechny možné nasazení mechanismy produkce XAML není povolena.</span><span class="sxs-lookup"><span data-stu-id="cb94c-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="cb94c-110">V konkrétních platforem (například WPF) musí být kód zkompilován.</span><span class="sxs-lookup"><span data-stu-id="cb94c-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="cb94c-111">V další architektury `x:Code` využití může být obecně zakázáno.</span><span class="sxs-lookup"><span data-stu-id="cb94c-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>  
  
 <span data-ttu-id="cb94c-112">Pro rozhraní, které umožňují spravované `x:Code` obsahu, kompilátor správný jazyk určený pro `x:Code` obsahu je vzhledem k nastavení a cíle obsahující projekt, který se používá ke kompilaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="cb94c-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="cb94c-113">Poznámky k použití WPF</span><span class="sxs-lookup"><span data-stu-id="cb94c-113">WPF Usage Notes</span></span>  
 <span data-ttu-id="cb94c-114">Kód deklarované v rámci `x:Code` pro WPF obsahuje několik významná omezení:</span><span class="sxs-lookup"><span data-stu-id="cb94c-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>  
  
- <span data-ttu-id="cb94c-115">`x:Code` – Element direktivy musí být bezprostřední podřízený element kořenového elementu XAML výroby.</span><span class="sxs-lookup"><span data-stu-id="cb94c-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>  
  
- <span data-ttu-id="cb94c-116">[x: Class – direktiva](x-class-directive.md) musí být zadaná na nadřazený kořenový element.</span><span class="sxs-lookup"><span data-stu-id="cb94c-116">[x:Class Directive](x-class-directive.md) must be provided on the parent root element.</span></span>  
  
- <span data-ttu-id="cb94c-117">Kód umístit `x:Code` kompilace musí být v rozsahu částečné třídy, která už se vytváří pro příslušnou stránku XAML se zpracuje.</span><span class="sxs-lookup"><span data-stu-id="cb94c-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="cb94c-118">Proto veškerý kód, který definujete musí být členy nebo proměnné částečné třídy.</span><span class="sxs-lookup"><span data-stu-id="cb94c-118">Therefore all code you define must be members or variables of that partial class.</span></span>  
  
- <span data-ttu-id="cb94c-119">Nejde definovat další třídy, jiné než pomocí vnoření třídy uvnitř částečné třídy (vnoření je povoleno, ale není obvyklé, protože vnořené třídy se nedá odkazovat v XAML).</span><span class="sxs-lookup"><span data-stu-id="cb94c-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="cb94c-120">Obory názvů CLR než obor názvů, který se používá pro existující částečné třídy nelze definované nebo přidat do.</span><span class="sxs-lookup"><span data-stu-id="cb94c-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>  
  
- <span data-ttu-id="cb94c-121">Odkazy na entity kód mimo obor názvů CLR částečné třídy musí být plně kvalifikovaný.</span><span class="sxs-lookup"><span data-stu-id="cb94c-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="cb94c-122">Pokud jsou členy deklarované přepsání na částečné třídy overridable členy, to musí být zadaný pomocí klíčové slovo override specifické pro jazyk.</span><span class="sxs-lookup"><span data-stu-id="cb94c-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="cb94c-123">Pokud členy deklarované v `x:Code` oboru v konfliktu s členy částečné třídy vytvořený mimo XAML, tak, že kompilátor oznámí konfliktu, soubor XAML nelze kompilovat nebo načíst.</span><span class="sxs-lookup"><span data-stu-id="cb94c-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb94c-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb94c-124">See also</span></span>

- [<span data-ttu-id="cb94c-125">x:Class – direktiva</span><span class="sxs-lookup"><span data-stu-id="cb94c-125">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="cb94c-126">Podkladový kód a kód XAML v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="cb94c-126">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="cb94c-127">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="cb94c-127">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
