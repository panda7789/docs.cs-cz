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
ms.openlocfilehash: 8fc5d1afd9e9723e6b3c58e100b0519ef8fdfab4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968366"
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="4d6fe-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d6fe-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="4d6fe-103">Určuje, že parametr procedury přijímá volitelné pole prvků zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="4d6fe-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="4d6fe-104">`ParamArray`dá se použít jenom pro poslední parametr seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="4d6fe-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d6fe-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d6fe-105">Remarks</span></span>  
 <span data-ttu-id="4d6fe-106">`ParamArray`umožňuje předat libovolnému počtu argumentů proceduru.</span><span class="sxs-lookup"><span data-stu-id="4d6fe-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="4d6fe-107">Parametr je vždy deklarován pomocí [ByVal.](../../../visual-basic/language-reference/modifiers/byval.md) `ParamArray`</span><span class="sxs-lookup"><span data-stu-id="4d6fe-107">A `ParamArray` parameter is always declared using [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
 <span data-ttu-id="4d6fe-108">Jednomu nebo více argumentům `ParamArray` můžete zadat parametr předáním pole vhodného datového typu, seznamu hodnot oddělených čárkami nebo nic vůbec.</span><span class="sxs-lookup"><span data-stu-id="4d6fe-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="4d6fe-109">Podrobnosti naleznete v tématu "volání ParamArray" v [polích parametrů](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="4d6fe-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4d6fe-110">Kdykoli budete pracovat s polem, které může být neomezeně velké, existuje riziko, že dojde k přeběhu některé interní kapacity vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="4d6fe-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="4d6fe-111">Pokud přijímáte pole parametrů z volajícího kódu, měli byste otestovat jeho délku a provést příslušné kroky, pokud je pro vaši aplikaci příliš velká.</span><span class="sxs-lookup"><span data-stu-id="4d6fe-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="4d6fe-112">V těchto kontextech lze použít Modifikátor:`ParamArray`</span><span class="sxs-lookup"><span data-stu-id="4d6fe-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="4d6fe-113">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="4d6fe-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="4d6fe-114">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="4d6fe-114">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="4d6fe-115">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="4d6fe-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="4d6fe-116">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="4d6fe-116">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="4d6fe-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d6fe-117">See also</span></span>

- [<span data-ttu-id="4d6fe-118">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="4d6fe-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="4d6fe-119">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="4d6fe-119">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
