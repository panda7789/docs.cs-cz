---
title: 'Postupy: Definice více verzí procedury'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: 870a18dbf3a7e28b7d7b612e853beeec6908cf6f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387930"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="96e58-102">Postupy: Definice více verzí procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96e58-102">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>
<span data-ttu-id="96e58-103">Můžete definovat proceduru v několika verzích tím, že je *převedete* pomocí stejného názvu, ale s jiným seznamem parametrů pro každou verzi.</span><span class="sxs-lookup"><span data-stu-id="96e58-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="96e58-104">Účelem přetížení je definovat několik úzce souvisejících verzí procedury bez nutnosti jejich rozlišení podle názvu.</span><span class="sxs-lookup"><span data-stu-id="96e58-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="96e58-105">Další informace najdete v tématu [přetížení procedury](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="96e58-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="96e58-106">Definování více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="96e58-106">To define multiple versions of a procedure</span></span>  
  
1. <span data-ttu-id="96e58-107">Zápis `Sub` příkazu nebo `Function` prohlášení pro každou verzi procedury, kterou chcete definovat.</span><span class="sxs-lookup"><span data-stu-id="96e58-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="96e58-108">Použijte stejný název procedury v každé deklaraci.</span><span class="sxs-lookup"><span data-stu-id="96e58-108">Use the same procedure name in every declaration.</span></span>  
  
2. <span data-ttu-id="96e58-109">Před `Sub` klíčovým slovem nebo `Function` v každé deklaraci pomocí klíčového slova [Overloads](../../../language-reference/modifiers/overloads.md) .</span><span class="sxs-lookup"><span data-stu-id="96e58-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="96e58-110">Volitelně můžete `Overloads` v deklaracích vynechat, ale pokud ji zahrnete do kterékoli deklarace, je nutné ji zahrnout do každé deklarace.</span><span class="sxs-lookup"><span data-stu-id="96e58-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3. <span data-ttu-id="96e58-111">Za každý příkaz deklarace, kód procedury zápisu pro zpracování konkrétního případu, kde volající kód dodá argumenty odpovídající seznamu parametrů verze.</span><span class="sxs-lookup"><span data-stu-id="96e58-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="96e58-112">Nemusíte testovat, které parametry zadal volající kód.</span><span class="sxs-lookup"><span data-stu-id="96e58-112">You do not have to test for which parameters the calling code has supplied.</span></span> <span data-ttu-id="96e58-113">Visual Basic předá řízení na vyhovující verzi vašeho postupu.</span><span class="sxs-lookup"><span data-stu-id="96e58-113">Visual Basic passes control to the matching version of your procedure.</span></span>  
  
4. <span data-ttu-id="96e58-114">V případě potřeby ukončete jednotlivé verze procedury pomocí `End Sub` `End Function` příkazu nebo.</span><span class="sxs-lookup"><span data-stu-id="96e58-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96e58-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="96e58-115">Example</span></span>  
 <span data-ttu-id="96e58-116">Následující příklad definuje `Sub` proceduru pro publikování transakce proti zůstatku zákazníka.</span><span class="sxs-lookup"><span data-stu-id="96e58-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="96e58-117">Pomocí `Overloads` klíčového slova definuje dvě verze procedury, jednu, která přijímá zákazníka podle názvu a druhý podle čísla účtu.</span><span class="sxs-lookup"><span data-stu-id="96e58-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 <span data-ttu-id="96e58-118">Volající kód může získat identifikaci zákazníka buď jako `String` nebo `Integer` , a pak použít stejný volající příkaz v obou případech.</span><span class="sxs-lookup"><span data-stu-id="96e58-118">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="96e58-119">Informace o tom, jak zavolat tyto verze `post` procedury, naleznete v tématu [How to: Call a Overloads](./how-to-call-an-overloaded-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="96e58-119">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="96e58-120">Kompilovat kód</span><span class="sxs-lookup"><span data-stu-id="96e58-120">Compile the code</span></span>  
 <span data-ttu-id="96e58-121">Ujistěte se, že všechny vaše přetížené verze mají stejný název procedury, ale jiný seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="96e58-121">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96e58-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="96e58-122">See also</span></span>

- [<span data-ttu-id="96e58-123">Procedury</span><span class="sxs-lookup"><span data-stu-id="96e58-123">Procedures</span></span>](./index.md)
- [<span data-ttu-id="96e58-124">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="96e58-124">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="96e58-125">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="96e58-125">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="96e58-126">Postupy: Přetížení procedury, která přebírá nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="96e58-126">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="96e58-127">Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů.</span><span class="sxs-lookup"><span data-stu-id="96e58-127">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="96e58-128">Aspekty přetížení procedur</span><span class="sxs-lookup"><span data-stu-id="96e58-128">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="96e58-129">Rozlišení přetěžování</span><span class="sxs-lookup"><span data-stu-id="96e58-129">Overload Resolution</span></span>](./overload-resolution.md)
