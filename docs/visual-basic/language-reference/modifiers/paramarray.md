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
ms.openlocfilehash: b9dee0fc876c6e7a02d085db7db4bf1c5dd2c68d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816653"
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="f11bf-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f11bf-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="f11bf-103">Určuje, že parametr procedury přijímá volitelné pole prvků zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="f11bf-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="f11bf-104">`ParamArray` lze použít pouze v posledním parametru seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="f11bf-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f11bf-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f11bf-105">Remarks</span></span>  
 <span data-ttu-id="f11bf-106">`ParamArray` umožňuje předat libovolný počet argumentů postup.</span><span class="sxs-lookup"><span data-stu-id="f11bf-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="f11bf-107">A `ParamArray` parametr je vždy deklarovány pomocí [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="f11bf-107">A `ParamArray` parameter is always declared using [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
 <span data-ttu-id="f11bf-108">Můžete zadat jednu nebo více argumentů `ParamArray` předáním pole odpovídající datový typ parametru, seznam hodnot, nebo nic vůbec.</span><span class="sxs-lookup"><span data-stu-id="f11bf-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="f11bf-109">Podrobnosti najdete v tématu "Volání ParamArray" [pole parametrů](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="f11bf-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f11bf-110">Pokaždé, když budete pracovat s polem, které mohou být po neomezenou dobu velké, existuje riziko přetečení vnitřní nějakým vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="f11bf-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="f11bf-111">Pokud souhlasíte s polem parametrů z volající kód, by měl test jeho délka a proveďte příslušné kroky, pokud je příliš velký pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f11bf-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="f11bf-112">`ParamArray` Modifikátor lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="f11bf-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="f11bf-113">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="f11bf-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="f11bf-114">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="f11bf-114">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="f11bf-115">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="f11bf-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="f11bf-116">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="f11bf-116">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="f11bf-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f11bf-117">See also</span></span>

- [<span data-ttu-id="f11bf-118">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="f11bf-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="f11bf-119">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="f11bf-119">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
