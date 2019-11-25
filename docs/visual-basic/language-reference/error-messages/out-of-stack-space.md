---
title: Nedostatek místa v zásobníku
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 9ae604a9727413f2705d42a4b68f5a50b7dd3feb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349186"
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="32c81-102">Nedostatek místa v zásobníku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32c81-102">Out of stack space (Visual Basic)</span></span>
<span data-ttu-id="32c81-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span><span class="sxs-lookup"><span data-stu-id="32c81-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="32c81-104">Its limits have been exceeded.</span><span class="sxs-lookup"><span data-stu-id="32c81-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="32c81-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="32c81-105">To correct this error</span></span>  
  
1. <span data-ttu-id="32c81-106">Check that procedures are not nested too deeply.</span><span class="sxs-lookup"><span data-stu-id="32c81-106">Check that procedures are not nested too deeply.</span></span>  
  
2. <span data-ttu-id="32c81-107">Make sure recursive procedures terminate properly.</span><span class="sxs-lookup"><span data-stu-id="32c81-107">Make sure recursive procedures terminate properly.</span></span>  
  
3. <span data-ttu-id="32c81-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span><span class="sxs-lookup"><span data-stu-id="32c81-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="32c81-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span><span class="sxs-lookup"><span data-stu-id="32c81-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="32c81-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span><span class="sxs-lookup"><span data-stu-id="32c81-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4. <span data-ttu-id="32c81-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span><span class="sxs-lookup"><span data-stu-id="32c81-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="32c81-112">You can also define the string at module level where it requires no stack space.</span><span class="sxs-lookup"><span data-stu-id="32c81-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5. <span data-ttu-id="32c81-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span><span class="sxs-lookup"><span data-stu-id="32c81-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6. <span data-ttu-id="32c81-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span><span class="sxs-lookup"><span data-stu-id="32c81-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="32c81-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by Visual Basic rather than an explicit call in the code.</span><span class="sxs-lookup"><span data-stu-id="32c81-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by Visual Basic rather than an explicit call in the code.</span></span> <span data-ttu-id="32c81-116">Use the `Calls` dialog box to view which procedures are active on the stack.</span><span class="sxs-lookup"><span data-stu-id="32c81-116">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32c81-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32c81-117">See also</span></span>

- [<span data-ttu-id="32c81-118">Okna paměti</span><span class="sxs-lookup"><span data-stu-id="32c81-118">Memory Windows</span></span>](/visualstudio/debugger/memory-windows)
