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
ms.openlocfilehash: f13fdae9617fa2af21978979cad6f90a15140a4a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969996"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="094aa-102">Postupy: Volání přetížené procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="094aa-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>
<span data-ttu-id="094aa-103">Výhodou přetížení procedury je flexibilitu volání.</span><span class="sxs-lookup"><span data-stu-id="094aa-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="094aa-104">Volající kód může získat informace, které je potřeba předat do procedury a poté zavolejte jedinou proceduru název, bez ohledu na to, jaké argumentů je předání.</span><span class="sxs-lookup"><span data-stu-id="094aa-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="094aa-105">Volání procedury, která má více než jednu verzi definovány</span><span class="sxs-lookup"><span data-stu-id="094aa-105">To call a procedure that has more than one version defined</span></span>  
  
1.  <span data-ttu-id="094aa-106">Ve volajícím kódu zjistěte, jaká data budou předány procesu.</span><span class="sxs-lookup"><span data-stu-id="094aa-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2.  <span data-ttu-id="094aa-107">Zápis protokolu TDS běžným způsobem, prezentování dat. v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="094aa-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="094aa-108">Ujistěte se, že argumenty odpovídat seznamu parametrů. v jednu z verzí definované pro proceduru.</span><span class="sxs-lookup"><span data-stu-id="094aa-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3.  <span data-ttu-id="094aa-109">Není nutné určit, která verze procedury pro volání.</span><span class="sxs-lookup"><span data-stu-id="094aa-109">You do not have to determine which version of the procedure to call.</span></span> <span data-ttu-id="094aa-110">Visual Basic předá řízení verzi, která odpovídá seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="094aa-110">Visual Basic passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="094aa-111">Následující příklad volá `post` postup deklarované v [jak: Definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="094aa-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="094aa-112">Získá Identifikace zákazníka, určuje, zda je `String` nebo `Integer`a poté v obou případech volá stejný postup.</span><span class="sxs-lookup"><span data-stu-id="094aa-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a><span data-ttu-id="094aa-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="094aa-113">See also</span></span>
- [<span data-ttu-id="094aa-114">Procedury</span><span class="sxs-lookup"><span data-stu-id="094aa-114">Procedures</span></span>](./index.md)
- [<span data-ttu-id="094aa-115">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="094aa-115">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="094aa-116">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="094aa-116">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="094aa-117">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="094aa-117">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="094aa-118">Postupy: Definice více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="094aa-118">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="094aa-119">Postupy: Přetížení procedury, která přebírá volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="094aa-119">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="094aa-120">Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů</span><span class="sxs-lookup"><span data-stu-id="094aa-120">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="094aa-121">Aspekty přetížení procedur</span><span class="sxs-lookup"><span data-stu-id="094aa-121">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="094aa-122">Řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="094aa-122">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="094aa-123">Overloads</span><span class="sxs-lookup"><span data-stu-id="094aa-123">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
