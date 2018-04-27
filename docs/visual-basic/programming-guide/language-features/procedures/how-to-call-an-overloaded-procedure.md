---
title: 'Postupy: Volání přetížené procedury (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5eca03de6b6dd2ca2b992196b1ae224f8fbf5068
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="5dd34-102">Postupy: Volání přetížené procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5dd34-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>
<span data-ttu-id="5dd34-103">Výhodou přetížení procedury je v flexibilitu volání.</span><span class="sxs-lookup"><span data-stu-id="5dd34-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="5dd34-104">Volání kódu můžete získat informace, které je nutné předat postupu a pak zavolají název jedinou proceduru, bez ohledu na to, jaké argumentů je předávání.</span><span class="sxs-lookup"><span data-stu-id="5dd34-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="5dd34-105">K volání procedury, která má definovaný více než jedna verze</span><span class="sxs-lookup"><span data-stu-id="5dd34-105">To call a procedure that has more than one version defined</span></span>  
  
1.  <span data-ttu-id="5dd34-106">Ve volání kódu určují, která data mají být předána do procesu.</span><span class="sxs-lookup"><span data-stu-id="5dd34-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2.  <span data-ttu-id="5dd34-107">Zápis volání procedury běžným způsobem, představuje data v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="5dd34-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="5dd34-108">Ujistěte se, že argumenty, které odpovídají seznam parametrů v jednom z verzí definované pro proceduru.</span><span class="sxs-lookup"><span data-stu-id="5dd34-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3.  <span data-ttu-id="5dd34-109">Nemusíte určit, která verze postup volání.</span><span class="sxs-lookup"><span data-stu-id="5dd34-109">You do not have to determine which version of the procedure to call.</span></span> <span data-ttu-id="5dd34-110">Visual Basic předá ovládacího prvku na verzi odpovídající vaší seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="5dd34-110">Visual Basic passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="5dd34-111">Následující příklad volání `post` postup deklarované v [postupy: definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="5dd34-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="5dd34-112">Ho získá Identifikace zákazníka, určuje, zda je `String` nebo `Integer`a potom v obou případech zavolá stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="5dd34-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5dd34-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="5dd34-113">See Also</span></span>  
 [<span data-ttu-id="5dd34-114">Procedury</span><span class="sxs-lookup"><span data-stu-id="5dd34-114">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="5dd34-115">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="5dd34-115">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="5dd34-116">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="5dd34-116">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="5dd34-117">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="5dd34-117">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="5dd34-118">Postupy: Definice více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="5dd34-118">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="5dd34-119">Postupy: Přetížení procedury, která přebírá nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="5dd34-119">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="5dd34-120">Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů</span><span class="sxs-lookup"><span data-stu-id="5dd34-120">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="5dd34-121">Aspekty přetížení procedur</span><span class="sxs-lookup"><span data-stu-id="5dd34-121">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)  
 [<span data-ttu-id="5dd34-122">Řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="5dd34-122">Overload Resolution</span></span>](./overload-resolution.md)  
 [<span data-ttu-id="5dd34-123">Overloads</span><span class="sxs-lookup"><span data-stu-id="5dd34-123">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
