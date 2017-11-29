---
title: ParamArray (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 06770f05aabedcf13cc9af1970a2c511a30c73b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="e6e70-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6e70-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="e6e70-103">Určuje, že parametr postupu přebírá volitelné pole elementy zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="e6e70-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="e6e70-104">`ParamArray`lze použít pouze na poslední parametr seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="e6e70-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6e70-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6e70-105">Remarks</span></span>  
 <span data-ttu-id="e6e70-106">`ParamArray`umožňuje předat libovolný počet argumentů procesu.</span><span class="sxs-lookup"><span data-stu-id="e6e70-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="e6e70-107">A `ParamArray` parametr je vždy deklarováno s použitím [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="e6e70-107">A `ParamArray` parameter is always declared using [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
 <span data-ttu-id="e6e70-108">Můžete zadat jednu nebo více argumentů `ParamArray` parametr předáním pole příslušná data typ, seznam hodnoty, nebo nic vůbec.</span><span class="sxs-lookup"><span data-stu-id="e6e70-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="e6e70-109">Podrobnosti najdete v tématu "Volání ParamArray" v [pole parametrů](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="e6e70-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e6e70-110">Vždy, když budete pracovat s pole to může být velký, bez omezení, existuje riziko překročení některé interní kapacitu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="e6e70-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="e6e70-111">Pokud přijmete pole parametrů z volání kódu, měli otestovat jeho délka a proveďte příslušné kroky, pokud je příliš velká pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e6e70-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="e6e70-112">`ParamArray` Modifikátor lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="e6e70-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="e6e70-113">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="e6e70-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="e6e70-114">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="e6e70-114">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="e6e70-115">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="e6e70-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="e6e70-116">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="e6e70-116">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="e6e70-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6e70-117">See Also</span></span>  
 [<span data-ttu-id="e6e70-118">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="e6e70-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="e6e70-119">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="e6e70-119">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
