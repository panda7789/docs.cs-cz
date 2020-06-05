---
title: ParamArray
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: e3c24818ea87884a0dd9b42c604e13e16ca6d3d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84391817"
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="ad39e-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad39e-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="ad39e-103">Určuje, že parametr procedury přijímá volitelné pole prvků zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="ad39e-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="ad39e-104">`ParamArray`dá se použít jenom pro poslední parametr seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="ad39e-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad39e-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad39e-105">Remarks</span></span>  
 <span data-ttu-id="ad39e-106">`ParamArray`umožňuje předat libovolnému počtu argumentů proceduru.</span><span class="sxs-lookup"><span data-stu-id="ad39e-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="ad39e-107">`ParamArray`Parametr je vždy deklarován pomocí [ByVal](byval.md).</span><span class="sxs-lookup"><span data-stu-id="ad39e-107">A `ParamArray` parameter is always declared using [ByVal](byval.md).</span></span>  
  
 <span data-ttu-id="ad39e-108">Jednomu nebo více argumentům můžete zadat `ParamArray` parametr předáním pole vhodného datového typu, seznamu hodnot oddělených čárkami nebo nic vůbec.</span><span class="sxs-lookup"><span data-stu-id="ad39e-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="ad39e-109">Podrobnosti naleznete v tématu "volání ParamArray" v [polích parametrů](../../programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="ad39e-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ad39e-110">Kdykoli budete pracovat s polem, které může být neomezeně velké, existuje riziko, že dojde k přeběhu některé interní kapacity vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="ad39e-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="ad39e-111">Pokud přijímáte pole parametrů z volajícího kódu, měli byste otestovat jeho délku a provést příslušné kroky, pokud je pro vaši aplikaci příliš velká.</span><span class="sxs-lookup"><span data-stu-id="ad39e-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="ad39e-112">`ParamArray`V těchto kontextech lze použít modifikátor:</span><span class="sxs-lookup"><span data-stu-id="ad39e-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="ad39e-113">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="ad39e-113">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="ad39e-114">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="ad39e-114">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="ad39e-115">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="ad39e-115">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="ad39e-116">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="ad39e-116">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="ad39e-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad39e-117">See also</span></span>

- [<span data-ttu-id="ad39e-118">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="ad39e-118">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="ad39e-119">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="ad39e-119">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
