---
title: ParamArray (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: be8ddb7f9ba08535d12890d1c5c82a9b7b485f3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597357"
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="781ed-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="781ed-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="781ed-103">Určuje, že parametr postupu přebírá volitelné pole elementy zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="781ed-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="781ed-104">`ParamArray` lze použít pouze na poslední parametr seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="781ed-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="781ed-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="781ed-105">Remarks</span></span>  
 <span data-ttu-id="781ed-106">`ParamArray` umožňuje předat libovolný počet argumentů procesu.</span><span class="sxs-lookup"><span data-stu-id="781ed-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="781ed-107">A `ParamArray` parametr je vždy deklarováno s použitím [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="781ed-107">A `ParamArray` parameter is always declared using [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
 <span data-ttu-id="781ed-108">Můžete zadat jednu nebo více argumentů `ParamArray` parametr předáním pole příslušná data typ, seznam hodnoty, nebo nic vůbec.</span><span class="sxs-lookup"><span data-stu-id="781ed-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="781ed-109">Podrobnosti najdete v tématu "Volání ParamArray" v [pole parametrů](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="781ed-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="781ed-110">Vždy, když budete pracovat s pole to může být velký, bez omezení, existuje riziko překročení některé interní kapacitu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="781ed-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="781ed-111">Pokud přijmete pole parametrů z volání kódu, měli otestovat jeho délka a proveďte příslušné kroky, pokud je příliš velká pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="781ed-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="781ed-112">`ParamArray` Modifikátor lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="781ed-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="781ed-113">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="781ed-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="781ed-114">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="781ed-114">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="781ed-115">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="781ed-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="781ed-116">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="781ed-116">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="781ed-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="781ed-117">See Also</span></span>  
 [<span data-ttu-id="781ed-118">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="781ed-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="781ed-119">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="781ed-119">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
