---
title: Procedura přetížení
ms.date: 07/20/2015
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
ms.openlocfilehash: 41a971896fe726cbe9849fd46334910e7288afe0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352590"
---
# <a name="procedure-overloading-visual-basic"></a><span data-ttu-id="60ac0-102">Procedura přetížení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60ac0-102">Procedure Overloading (Visual Basic)</span></span>

<span data-ttu-id="60ac0-103">*Přetížení* procedury znamená, že ji definují v několika verzích se stejným názvem, ale s různými seznamy parametrů.</span><span class="sxs-lookup"><span data-stu-id="60ac0-103">*Overloading* a procedure means defining it in multiple versions, using the same name but different parameter lists.</span></span> <span data-ttu-id="60ac0-104">Účelem přetížení je definovat několik úzce souvisejících verzí procedury bez nutnosti jejich rozlišení podle názvu.</span><span class="sxs-lookup"><span data-stu-id="60ac0-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span> <span data-ttu-id="60ac0-105">Provedete to tak, že změníte seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="60ac0-105">You do this by varying the parameter list.</span></span>

## <a name="overloading-rules"></a><span data-ttu-id="60ac0-106">Pravidla přetížení</span><span class="sxs-lookup"><span data-stu-id="60ac0-106">Overloading Rules</span></span>

<span data-ttu-id="60ac0-107">Při přetížení procedury platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="60ac0-107">When you overload a procedure, the following rules apply:</span></span>

- <span data-ttu-id="60ac0-108">**Stejný název**.</span><span class="sxs-lookup"><span data-stu-id="60ac0-108">**Same Name**.</span></span> <span data-ttu-id="60ac0-109">Každá přetížená verze musí používat stejný název procedury.</span><span class="sxs-lookup"><span data-stu-id="60ac0-109">Each overloaded version must use the same procedure name.</span></span>

- <span data-ttu-id="60ac0-110">**Jiný podpis**.</span><span class="sxs-lookup"><span data-stu-id="60ac0-110">**Different Signature**.</span></span> <span data-ttu-id="60ac0-111">Každá přetížená verze se musí lišit od všech ostatních přetížených verzí alespoň v jednom z následujících hledisek:</span><span class="sxs-lookup"><span data-stu-id="60ac0-111">Each overloaded version must differ from all other overloaded versions in at least one of the following respects:</span></span>

  - <span data-ttu-id="60ac0-112">Počet parametrů</span><span class="sxs-lookup"><span data-stu-id="60ac0-112">Number of parameters</span></span>

  - <span data-ttu-id="60ac0-113">Pořadí parametrů</span><span class="sxs-lookup"><span data-stu-id="60ac0-113">Order of the parameters</span></span>

  - <span data-ttu-id="60ac0-114">Datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="60ac0-114">Data types of the parameters</span></span>

  - <span data-ttu-id="60ac0-115">Počet parametrů typu (pro obecný postup)</span><span class="sxs-lookup"><span data-stu-id="60ac0-115">Number of type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="60ac0-116">Návratový typ (jenom pro operátor převodu)</span><span class="sxs-lookup"><span data-stu-id="60ac0-116">Return type (only for a conversion operator)</span></span>

  <span data-ttu-id="60ac0-117">Spolu s názvem procedury jsou předchozí položky souhrnně označovány jako *podpis* procedury.</span><span class="sxs-lookup"><span data-stu-id="60ac0-117">Together with the procedure name, the preceding items are collectively called the *signature* of the procedure.</span></span> <span data-ttu-id="60ac0-118">Při volání přetížené procedury kompilátor používá signaturu k ověření, že volání správně odpovídá definici.</span><span class="sxs-lookup"><span data-stu-id="60ac0-118">When you call an overloaded procedure, the compiler uses the signature to check that the call correctly matches the definition.</span></span>

- <span data-ttu-id="60ac0-119">**Položky, které nejsou součástí podpisu**.</span><span class="sxs-lookup"><span data-stu-id="60ac0-119">**Items Not Part of Signature**.</span></span> <span data-ttu-id="60ac0-120">Nemůžete přetížit proceduru bez proměnlivého podpisu.</span><span class="sxs-lookup"><span data-stu-id="60ac0-120">You cannot overload a procedure without varying the signature.</span></span> <span data-ttu-id="60ac0-121">Konkrétně nemůžete přetížit proceduru změnou pouze jedné nebo více z následujících položek:</span><span class="sxs-lookup"><span data-stu-id="60ac0-121">In particular, you cannot overload a procedure by varying only one or more of the following items:</span></span>

  - <span data-ttu-id="60ac0-122">Klíčová slova modifikátoru procedury, například `Public`, `Shared`a `Static`</span><span class="sxs-lookup"><span data-stu-id="60ac0-122">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>

  - <span data-ttu-id="60ac0-123">Parametry nebo názvy parametrů typu</span><span class="sxs-lookup"><span data-stu-id="60ac0-123">Parameter or type parameter names</span></span>

  - <span data-ttu-id="60ac0-124">Omezení parametru typu (pro obecný postup)</span><span class="sxs-lookup"><span data-stu-id="60ac0-124">Type parameter constraints (for a generic procedure)</span></span>

  - <span data-ttu-id="60ac0-125">Klíčová slova modifikátoru parametru, například `ByRef` a `Optional`</span><span class="sxs-lookup"><span data-stu-id="60ac0-125">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>

  - <span data-ttu-id="60ac0-126">Bez ohledu na to, zda vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="60ac0-126">Whether it returns a value</span></span>

  - <span data-ttu-id="60ac0-127">Datový typ návratové hodnoty (s výjimkou operátoru převodu)</span><span class="sxs-lookup"><span data-stu-id="60ac0-127">The data type of the return value (except for a conversion operator)</span></span>

  <span data-ttu-id="60ac0-128">Položky v předchozím seznamu nejsou součástí signatury.</span><span class="sxs-lookup"><span data-stu-id="60ac0-128">The items in the preceding list are not part of the signature.</span></span> <span data-ttu-id="60ac0-129">I když je nemůžete použít k rozlišení mezi přetíženými verzemi, můžete je měnit mezi přetíženými verzemi, které jsou správně odlišeny svými podpisy.</span><span class="sxs-lookup"><span data-stu-id="60ac0-129">Although you cannot use them to differentiate between overloaded versions, you can vary them among overloaded versions that are properly differentiated by their signatures.</span></span>

- <span data-ttu-id="60ac0-130">**Argumenty s pozdní vazbou**.</span><span class="sxs-lookup"><span data-stu-id="60ac0-130">**Late-Bound Arguments**.</span></span> <span data-ttu-id="60ac0-131">Pokud máte v úmyslu předat proměnnou s pozdní vazbou objektu do přetížené verze, je nutné deklarovat příslušný parametr jako <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="60ac0-131">If you intend to pass a late bound object variable to an overloaded version, you must declare the appropriate parameter as <xref:System.Object>.</span></span>

## <a name="multiple-versions-of-a-procedure"></a><span data-ttu-id="60ac0-132">Více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="60ac0-132">Multiple Versions of a Procedure</span></span>

<span data-ttu-id="60ac0-133">Předpokládejme, že píšete `Sub` postup pro publikování transakce proti zůstatku zákazníka a chcete být schopni odkazovat na zákazníka buď podle jména, nebo podle čísla účtu.</span><span class="sxs-lookup"><span data-stu-id="60ac0-133">Suppose you are writing a `Sub` procedure to post a transaction against a customer's balance, and you want to be able to refer to the customer either by name or by account number.</span></span> <span data-ttu-id="60ac0-134">Chcete-li to přizpůsobit, můžete definovat dva různé `Sub` postupy, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="60ac0-134">To accommodate this, you can define two different `Sub` procedures, as in the following example:</span></span>

[!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]

### <a name="overloaded-versions"></a><span data-ttu-id="60ac0-135">Přetížené verze</span><span class="sxs-lookup"><span data-stu-id="60ac0-135">Overloaded Versions</span></span>

<span data-ttu-id="60ac0-136">Alternativou je přetížení jednoho názvu procedury.</span><span class="sxs-lookup"><span data-stu-id="60ac0-136">An alternative is to overload a single procedure name.</span></span> <span data-ttu-id="60ac0-137">Pomocí klíčového slova [přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md) můžete definovat verzi procedury pro každý seznam parametrů následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="60ac0-137">You can use the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword to define a version of the procedure for each parameter list, as follows:</span></span>

[!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]

#### <a name="additional-overloads"></a><span data-ttu-id="60ac0-138">Další přetížení</span><span class="sxs-lookup"><span data-stu-id="60ac0-138">Additional Overloads</span></span>

<span data-ttu-id="60ac0-139">Pokud jste také chtěli přijmout částku transakce buď v `Decimal` nebo `Single`, můžete další přetížení `post`, abyste tuto variaci povolili.</span><span class="sxs-lookup"><span data-stu-id="60ac0-139">If you also wanted to accept a transaction amount in either `Decimal` or `Single`, you could further overload `post` to allow for this variation.</span></span> <span data-ttu-id="60ac0-140">Pokud jste to nastavili pro každé přetížení v předchozím příkladu, měli byste mít čtyři `Sub` postupy, všechny se stejným názvem, ale se čtyřmi různými podpisy.</span><span class="sxs-lookup"><span data-stu-id="60ac0-140">If you did this to each of the overloads in the preceding example, you would have four `Sub` procedures, all with the same name but with four different signatures.</span></span>

## <a name="advantages-of-overloading"></a><span data-ttu-id="60ac0-141">Výhody přetížení</span><span class="sxs-lookup"><span data-stu-id="60ac0-141">Advantages of Overloading</span></span>

<span data-ttu-id="60ac0-142">Výhodou přetížení procedury je flexibilita volání.</span><span class="sxs-lookup"><span data-stu-id="60ac0-142">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="60ac0-143">Chcete-li použít `post` procedury deklarované v předchozím příkladu, volající kód může získat identifikaci zákazníka buď jako `String` nebo `Integer`, a pak volat stejný postup v obou případech.</span><span class="sxs-lookup"><span data-stu-id="60ac0-143">To use the `post` procedure declared in the preceding example, the calling code can obtain the customer identification as either a `String` or an `Integer`, and then call the same procedure in either case.</span></span> <span data-ttu-id="60ac0-144">Následující příklad znázorňuje toto:</span><span class="sxs-lookup"><span data-stu-id="60ac0-144">The following example illustrates this:</span></span>

[!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]

[!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]

## <a name="see-also"></a><span data-ttu-id="60ac0-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60ac0-145">See also</span></span>

- [<span data-ttu-id="60ac0-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="60ac0-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="60ac0-147">Postupy: Definice více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="60ac0-147">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="60ac0-148">Postupy: Volání přetížené procedury</span><span class="sxs-lookup"><span data-stu-id="60ac0-148">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="60ac0-149">Postupy: Přetížení procedury, která přebírá nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="60ac0-149">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="60ac0-150">Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů</span><span class="sxs-lookup"><span data-stu-id="60ac0-150">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="60ac0-151">Aspekty přetížení procedur</span><span class="sxs-lookup"><span data-stu-id="60ac0-151">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="60ac0-152">Řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="60ac0-152">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="60ac0-153">Overloads</span><span class="sxs-lookup"><span data-stu-id="60ac0-153">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="60ac0-154">Obecné typy v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="60ac0-154">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
