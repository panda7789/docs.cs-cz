---
title: 'Postupy: Volání přetížené procedury'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: d983f5f6183c33141079ed35171f7a73f254450f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340199"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="3c0c6-102">Postupy: Volání přetížené procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c0c6-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>
<span data-ttu-id="3c0c6-103">The advantage of overloading a procedure is in the flexibility of the call.</span><span class="sxs-lookup"><span data-stu-id="3c0c6-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="3c0c6-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span><span class="sxs-lookup"><span data-stu-id="3c0c6-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="3c0c6-105">To call a procedure that has more than one version defined</span><span class="sxs-lookup"><span data-stu-id="3c0c6-105">To call a procedure that has more than one version defined</span></span>  
  
1. <span data-ttu-id="3c0c6-106">In the calling code, determine which data to pass to the procedure.</span><span class="sxs-lookup"><span data-stu-id="3c0c6-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2. <span data-ttu-id="3c0c6-107">Write the procedure call in the normal way, presenting the data in the argument list.</span><span class="sxs-lookup"><span data-stu-id="3c0c6-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="3c0c6-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span><span class="sxs-lookup"><span data-stu-id="3c0c6-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3. <span data-ttu-id="3c0c6-109">You do not have to determine which version of the procedure to call.</span><span class="sxs-lookup"><span data-stu-id="3c0c6-109">You do not have to determine which version of the procedure to call.</span></span> <span data-ttu-id="3c0c6-110">Visual Basic passes control to the version matching your argument list.</span><span class="sxs-lookup"><span data-stu-id="3c0c6-110">Visual Basic passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="3c0c6-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="3c0c6-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="3c0c6-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span><span class="sxs-lookup"><span data-stu-id="3c0c6-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a><span data-ttu-id="3c0c6-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c0c6-113">See also</span></span>

- [<span data-ttu-id="3c0c6-114">Procedury</span><span class="sxs-lookup"><span data-stu-id="3c0c6-114">Procedures</span></span>](./index.md)
- [<span data-ttu-id="3c0c6-115">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="3c0c6-115">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="3c0c6-116">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="3c0c6-116">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="3c0c6-117">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="3c0c6-117">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="3c0c6-118">Postupy: Definice více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="3c0c6-118">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="3c0c6-119">Postupy: Přetížení procedury, která přebírá nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="3c0c6-119">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="3c0c6-120">Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů</span><span class="sxs-lookup"><span data-stu-id="3c0c6-120">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="3c0c6-121">Aspekty přetížení procedur</span><span class="sxs-lookup"><span data-stu-id="3c0c6-121">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="3c0c6-122">Řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="3c0c6-122">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="3c0c6-123">Overloads</span><span class="sxs-lookup"><span data-stu-id="3c0c6-123">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
