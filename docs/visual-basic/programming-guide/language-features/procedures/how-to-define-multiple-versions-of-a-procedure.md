---
title: 'Postupy: Definice více verzí procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: a4d0c5bbb07dd5433ff62179fc10a6274bf19364
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649809"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="296e5-102">Postupy: Definice více verzí procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="296e5-102">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>
<span data-ttu-id="296e5-103">Můžete definovat procedury ve více verzí podle *přetížení* jeho pomocí se stejným názvem, ale seznam různých parametrů pro každou verzi.</span><span class="sxs-lookup"><span data-stu-id="296e5-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="296e5-104">Účelem přetížení je definovat několik úzce související verzí procedury bez nutnosti jejich odlišení podle názvu.</span><span class="sxs-lookup"><span data-stu-id="296e5-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="296e5-105">Další informace najdete v tématu [přetížení procedury](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="296e5-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="296e5-106">Chcete-li definovat více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="296e5-106">To define multiple versions of a procedure</span></span>  
  
1.  <span data-ttu-id="296e5-107">Zápis `Sub` nebo `Function` příkaz deklarace pro každou verzi postupu chcete definovat.</span><span class="sxs-lookup"><span data-stu-id="296e5-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="296e5-108">Použijte stejný název procedury v každé deklaraci.</span><span class="sxs-lookup"><span data-stu-id="296e5-108">Use the same procedure name in every declaration.</span></span>  
  
2.  <span data-ttu-id="296e5-109">Předcházet `Sub` nebo `Function` – klíčové slovo v každé deklarace s [přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="296e5-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="296e5-110">Volitelně můžete vynechat `Overloads` v deklaracích, ale pokud můžete zahrnout v některém z deklarací, je třeba jej zahrnout v každé deklaraci.</span><span class="sxs-lookup"><span data-stu-id="296e5-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3.  <span data-ttu-id="296e5-111">Následující každý příkaz deklarace napište kód postup pro zpracování konkrétní případ, kdy kód volání poskytuje argumenty odpovídající seznam parametrů této verze.</span><span class="sxs-lookup"><span data-stu-id="296e5-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="296e5-112">Nemáte k testování pro parametry, které má zadaný kód volání.</span><span class="sxs-lookup"><span data-stu-id="296e5-112">You do not have to test for which parameters the calling code has supplied.</span></span> <span data-ttu-id="296e5-113">Visual Basic předá řízení na odpovídající verzi vaší procedury.</span><span class="sxs-lookup"><span data-stu-id="296e5-113">Visual Basic passes control to the matching version of your procedure.</span></span>  
  
4.  <span data-ttu-id="296e5-114">Ukončit jednotlivých verzí procedury s `End Sub` nebo `End Function` příkaz podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="296e5-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="296e5-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="296e5-115">Example</span></span>  
 <span data-ttu-id="296e5-116">V následujícím příkladu definuje `Sub` postup post transakce proti zůstatku zákazníka.</span><span class="sxs-lookup"><span data-stu-id="296e5-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="296e5-117">Použije `Overloads` – klíčové slovo definovat dvě verze postup, který přijímá zákazník podle názvu a dalších číslem účet.</span><span class="sxs-lookup"><span data-stu-id="296e5-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]  
  
 <span data-ttu-id="296e5-118">Volání kódu můžete získat Identifikace zákazníka jako buď `String` nebo `Integer`a potom pomocí stejné volání příkazu v obou případech.</span><span class="sxs-lookup"><span data-stu-id="296e5-118">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="296e5-119">Informace o tom, jak volat tyto verze nástroje `post` postupu najdete v části [postupy: volání přetížené procedury](./how-to-call-an-overloaded-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="296e5-119">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="296e5-120">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="296e5-120">Compiling the Code</span></span>  
 <span data-ttu-id="296e5-121">Zajistěte, aby že každý přetížené verze má stejný název postupu, ale seznam různých parametrů.</span><span class="sxs-lookup"><span data-stu-id="296e5-121">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="296e5-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="296e5-122">See Also</span></span>  
 [<span data-ttu-id="296e5-123">Procedury</span><span class="sxs-lookup"><span data-stu-id="296e5-123">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="296e5-124">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="296e5-124">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="296e5-125">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="296e5-125">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="296e5-126">Postupy: Přetížení procedury, která přebírá nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="296e5-126">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="296e5-127">Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů</span><span class="sxs-lookup"><span data-stu-id="296e5-127">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="296e5-128">Aspekty přetížení procedur</span><span class="sxs-lookup"><span data-stu-id="296e5-128">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)  
 [<span data-ttu-id="296e5-129">Řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="296e5-129">Overload Resolution</span></span>](./overload-resolution.md)
