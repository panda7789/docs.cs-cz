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
ms.openlocfilehash: fbc87bffebc265e6062512e96fc29a64334b3c65
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351376"
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="320b4-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="320b4-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="320b4-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span><span class="sxs-lookup"><span data-stu-id="320b4-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="320b4-104">`ParamArray` can be used only on the last parameter of a parameter list.</span><span class="sxs-lookup"><span data-stu-id="320b4-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="320b4-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="320b4-105">Remarks</span></span>  
 <span data-ttu-id="320b4-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span><span class="sxs-lookup"><span data-stu-id="320b4-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="320b4-107">A `ParamArray` parameter is always declared using [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="320b4-107">A `ParamArray` parameter is always declared using [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
 <span data-ttu-id="320b4-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span><span class="sxs-lookup"><span data-stu-id="320b4-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="320b4-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="320b4-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="320b4-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span><span class="sxs-lookup"><span data-stu-id="320b4-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="320b4-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span><span class="sxs-lookup"><span data-stu-id="320b4-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="320b4-112">The `ParamArray` modifier can be used in these contexts:</span><span class="sxs-lookup"><span data-stu-id="320b4-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="320b4-113">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="320b4-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="320b4-114">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="320b4-114">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="320b4-115">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="320b4-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="320b4-116">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="320b4-116">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="320b4-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="320b4-117">See also</span></span>

- [<span data-ttu-id="320b4-118">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="320b4-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="320b4-119">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="320b4-119">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
