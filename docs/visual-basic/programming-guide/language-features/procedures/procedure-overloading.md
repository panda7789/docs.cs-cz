---
title: Procedura přetížení (Visual Basic)
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
ms.openlocfilehash: 3cb11079241da4815c6e7bde4a76123965a95514
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712519"
---
# <a name="procedure-overloading-visual-basic"></a><span data-ttu-id="ceb7d-102">Procedura přetížení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ceb7d-102">Procedure Overloading (Visual Basic)</span></span>
<span data-ttu-id="ceb7d-103">*Přetížení* postup znamená, že jeho definováním v více verzí pomocí stejného názvu, ale seznamy různých parametrů.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-103">*Overloading* a procedure means defining it in multiple versions, using the same name but different parameter lists.</span></span> <span data-ttu-id="ceb7d-104">Účelem přetížení je definovat několik úzce související verze procedury, aniž byste museli rozlišit podle názvu.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span> <span data-ttu-id="ceb7d-105">Můžete to provést pomocí různých seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-105">You do this by varying the parameter list.</span></span>  
  
## <a name="overloading-rules"></a><span data-ttu-id="ceb7d-106">Přetížení pravidla</span><span class="sxs-lookup"><span data-stu-id="ceb7d-106">Overloading Rules</span></span>  
 <span data-ttu-id="ceb7d-107">Když je přetížení procedury, platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="ceb7d-107">When you overload a procedure, the following rules apply:</span></span>  
  
-   <span data-ttu-id="ceb7d-108">**Stejný název**.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-108">**Same Name**.</span></span> <span data-ttu-id="ceb7d-109">Všechny přetížené verze, musíte použít stejný název procedury.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-109">Each overloaded version must use the same procedure name.</span></span>  
  
-   <span data-ttu-id="ceb7d-110">**Jiný podpis**.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-110">**Different Signature**.</span></span> <span data-ttu-id="ceb7d-111">Všechny přetížené verze se musí lišit od jiných přetížené verze alespoň v jedné z těchto ohledech:</span><span class="sxs-lookup"><span data-stu-id="ceb7d-111">Each overloaded version must differ from all other overloaded versions in at least one of the following respects:</span></span>  
  
    -   <span data-ttu-id="ceb7d-112">Počet parametrů</span><span class="sxs-lookup"><span data-stu-id="ceb7d-112">Number of parameters</span></span>  
  
    -   <span data-ttu-id="ceb7d-113">Pořadí parametrů</span><span class="sxs-lookup"><span data-stu-id="ceb7d-113">Order of the parameters</span></span>  
  
    -   <span data-ttu-id="ceb7d-114">Datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="ceb7d-114">Data types of the parameters</span></span>  
  
    -   <span data-ttu-id="ceb7d-115">Počet parametrů typu (pro obecný postup)</span><span class="sxs-lookup"><span data-stu-id="ceb7d-115">Number of type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="ceb7d-116">Návratový typ (pouze pro operátor převodu)</span><span class="sxs-lookup"><span data-stu-id="ceb7d-116">Return type (only for a conversion operator)</span></span>  
  
     <span data-ttu-id="ceb7d-117">Spolu s názvem procedury se společně nazývají předchozí položky *podpis* procedury.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-117">Together with the procedure name, the preceding items are collectively called the *signature* of the procedure.</span></span> <span data-ttu-id="ceb7d-118">Při volání přetížené procedury kompilátor používá ke kontrole, jestli volání správně odpovídá definici podpis.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-118">When you call an overloaded procedure, the compiler uses the signature to check that the call correctly matches the definition.</span></span>  
  
-   <span data-ttu-id="ceb7d-119">**Položky není součástí podpis**.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-119">**Items Not Part of Signature**.</span></span> <span data-ttu-id="ceb7d-120">Bez různé podpis nelze přetížení procedury.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-120">You cannot overload a procedure without varying the signature.</span></span> <span data-ttu-id="ceb7d-121">Konkrétně se nemůže přetížení procedury změnou pouze jeden nebo více z následujících položek:</span><span class="sxs-lookup"><span data-stu-id="ceb7d-121">In particular, you cannot overload a procedure by varying only one or more of the following items:</span></span>  
  
    -   <span data-ttu-id="ceb7d-122">Postup modifikátor klíčová slova, jako například `Public`, `Shared`, a `Static`</span><span class="sxs-lookup"><span data-stu-id="ceb7d-122">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>  
  
    -   <span data-ttu-id="ceb7d-123">Názvy parametrů parametru nebo typ</span><span class="sxs-lookup"><span data-stu-id="ceb7d-123">Parameter or type parameter names</span></span>  
  
    -   <span data-ttu-id="ceb7d-124">Omezení parametru typu (pro obecný postup)</span><span class="sxs-lookup"><span data-stu-id="ceb7d-124">Type parameter constraints (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="ceb7d-125">Klíčová slova modifikátor parametru, jako například `ByRef` a `Optional`</span><span class="sxs-lookup"><span data-stu-id="ceb7d-125">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>  
  
    -   <span data-ttu-id="ceb7d-126">Určuje, zda vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="ceb7d-126">Whether it returns a value</span></span>  
  
    -   <span data-ttu-id="ceb7d-127">Datový typ vrácené hodnoty (s výjimkou operátoru převodu)</span><span class="sxs-lookup"><span data-stu-id="ceb7d-127">The data type of the return value (except for a conversion operator)</span></span>  
  
     <span data-ttu-id="ceb7d-128">Položky v předchozím seznamu nejsou součást podpisu.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-128">The items in the preceding list are not part of the signature.</span></span> <span data-ttu-id="ceb7d-129">I když nelze je použít k rozlišení mezi přetížené verze, můžete je lišit mezi přetížené verze, které jsou správně rozlišené pomocí jejich podpisy.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-129">Although you cannot use them to differentiate between overloaded versions, you can vary them among overloaded versions that are properly differentiated by their signatures.</span></span>  
  
-   <span data-ttu-id="ceb7d-130">**S pozdní vazbou argumenty**.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-130">**Late-Bound Arguments**.</span></span> <span data-ttu-id="ceb7d-131">Pokud máte v úmyslu pozdní vazbou objektové proměnné předat přetížené verze, je třeba deklarovat jako odpovídající parametr <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-131">If you intend to pass a late bound object variable to an overloaded version, you must declare the appropriate parameter as <xref:System.Object>.</span></span>  
  
## <a name="multiple-versions-of-a-procedure"></a><span data-ttu-id="ceb7d-132">Více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="ceb7d-132">Multiple Versions of a Procedure</span></span>  
 <span data-ttu-id="ceb7d-133">Předpokládejme, že vytváříte `Sub` postup pro transakci proti zůstatek zákazníka a chtějí mít možnost odkazovat na zákazníka, název nebo číslo účtu.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-133">Suppose you are writing a `Sub` procedure to post a transaction against a customer's balance, and you want to be able to refer to the customer either by name or by account number.</span></span> <span data-ttu-id="ceb7d-134">K tomuto účelu můžete definovat dva různé `Sub` postupy, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ceb7d-134">To accommodate this, you can define two different `Sub` procedures, as in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#73](./codesnippet/VisualBasic/procedure-overloading_1.vb)]  
  
### <a name="overloaded-versions"></a><span data-ttu-id="ceb7d-135">Přetížené verze</span><span class="sxs-lookup"><span data-stu-id="ceb7d-135">Overloaded Versions</span></span>  
 <span data-ttu-id="ceb7d-136">Alternativou je přetížení název jedinou proceduru.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-136">An alternative is to overload a single procedure name.</span></span> <span data-ttu-id="ceb7d-137">Můžete použít [přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md) – klíčové slovo k definování verzi postup pro každý seznam parametrů, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ceb7d-137">You can use the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword to define a version of the procedure for each parameter list, as follows:</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/procedure-overloading_2.vb)]  
  
#### <a name="additional-overloads"></a><span data-ttu-id="ceb7d-138">Další přetížení</span><span class="sxs-lookup"><span data-stu-id="ceb7d-138">Additional Overloads</span></span>  
 <span data-ttu-id="ceb7d-139">Pokud byste chtěli také tak, aby přijímal částka transakce buď `Decimal` nebo `Single`, může další přetížení `post` povolit pro tuto variaci.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-139">If you also wanted to accept a transaction amount in either `Decimal` or `Single`, you could further overload `post` to allow for this variation.</span></span> <span data-ttu-id="ceb7d-140">Pokud jste to udělali u každého z přetížení v předchozím příkladu, byste měli čtyři `Sub` postupy, všechny se stejným názvem, ale s různými signaturami čtyři.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-140">If you did this to each of the overloads in the preceding example, you would have four `Sub` procedures, all with the same name but with four different signatures.</span></span>  
  
## <a name="advantages-of-overloading"></a><span data-ttu-id="ceb7d-141">Výhody přetížení</span><span class="sxs-lookup"><span data-stu-id="ceb7d-141">Advantages of Overloading</span></span>  
 <span data-ttu-id="ceb7d-142">Výhodou přetížení procedury je flexibilitu volání.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-142">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="ceb7d-143">Použít `post` postup deklarované v předchozím příkladu, volající kód může získat Identifikace zákazníka jako buď `String` nebo `Integer`a následně zavolat stejný postup v obou případech.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-143">To use the `post` procedure declared in the preceding example, the calling code can obtain the customer identification as either a `String` or an `Integer`, and then call the same procedure in either case.</span></span> <span data-ttu-id="ceb7d-144">Následující příklad ukazuje toto:</span><span class="sxs-lookup"><span data-stu-id="ceb7d-144">The following example illustrates this:</span></span>  
  
 [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/procedure-overloading_3.vb)]  
  
 [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/procedure-overloading_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ceb7d-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ceb7d-145">See also</span></span>
- [<span data-ttu-id="ceb7d-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="ceb7d-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="ceb7d-147">Postupy: Definice více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="ceb7d-147">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="ceb7d-148">Postupy: Volání přetížené procedury</span><span class="sxs-lookup"><span data-stu-id="ceb7d-148">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="ceb7d-149">Postupy: Přetížení procedury, která přebírá volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="ceb7d-149">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="ceb7d-150">Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů</span><span class="sxs-lookup"><span data-stu-id="ceb7d-150">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="ceb7d-151">Aspekty přetížení procedur</span><span class="sxs-lookup"><span data-stu-id="ceb7d-151">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="ceb7d-152">Řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="ceb7d-152">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="ceb7d-153">Overloads</span><span class="sxs-lookup"><span data-stu-id="ceb7d-153">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="ceb7d-154">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ceb7d-154">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
