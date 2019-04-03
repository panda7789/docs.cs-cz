---
title: 'Postupy: Volání přetížené procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: 9dda0fbc0cffe8904ab97c46cea40d5cf00c91e9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843783"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="7bac8-102">Postupy: Volání přetížené procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bac8-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>
<span data-ttu-id="7bac8-103">Výhodou přetížení procedury je flexibilitu volání.</span><span class="sxs-lookup"><span data-stu-id="7bac8-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="7bac8-104">Volající kód může získat informace, které je potřeba předat do procedury a poté zavolejte jedinou proceduru název, bez ohledu na to, jaké argumentů je předání.</span><span class="sxs-lookup"><span data-stu-id="7bac8-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="7bac8-105">Volání procedury, která má více než jednu verzi definovány</span><span class="sxs-lookup"><span data-stu-id="7bac8-105">To call a procedure that has more than one version defined</span></span>  
  
1.  <span data-ttu-id="7bac8-106">Ve volajícím kódu zjistěte, jaká data budou předány procesu.</span><span class="sxs-lookup"><span data-stu-id="7bac8-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2.  <span data-ttu-id="7bac8-107">Zápis protokolu TDS běžným způsobem, prezentování dat. v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="7bac8-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="7bac8-108">Ujistěte se, že argumenty odpovídat seznamu parametrů. v jednu z verzí definované pro proceduru.</span><span class="sxs-lookup"><span data-stu-id="7bac8-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3.  <span data-ttu-id="7bac8-109">Není nutné určit, která verze procedury pro volání.</span><span class="sxs-lookup"><span data-stu-id="7bac8-109">You do not have to determine which version of the procedure to call.</span></span> <span data-ttu-id="7bac8-110">Visual Basic předá řízení verzi, která odpovídá seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="7bac8-110">Visual Basic passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="7bac8-111">Následující příklad volá `post` postup deklarované v [jak: Definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="7bac8-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="7bac8-112">Získá Identifikace zákazníka, určuje, zda je `String` nebo `Integer`a poté v obou případech volá stejný postup.</span><span class="sxs-lookup"><span data-stu-id="7bac8-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a><span data-ttu-id="7bac8-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7bac8-113">See also</span></span>

- [<span data-ttu-id="7bac8-114">Procedury</span><span class="sxs-lookup"><span data-stu-id="7bac8-114">Procedures</span></span>](./index.md)
- [<span data-ttu-id="7bac8-115">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="7bac8-115">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="7bac8-116">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="7bac8-116">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="7bac8-117">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="7bac8-117">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="7bac8-118">Postupy: Definice více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="7bac8-118">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="7bac8-119">Postupy: Přetížení procedury, která přebírá volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="7bac8-119">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="7bac8-120">Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů</span><span class="sxs-lookup"><span data-stu-id="7bac8-120">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="7bac8-121">Aspekty přetížení procedur</span><span class="sxs-lookup"><span data-stu-id="7bac8-121">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="7bac8-122">Řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="7bac8-122">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="7bac8-123">Overloads</span><span class="sxs-lookup"><span data-stu-id="7bac8-123">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
