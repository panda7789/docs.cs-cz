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
ms.openlocfilehash: 0d1f2c4d8c88922659b3d91ed41d5e760e6e5233
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653911"
---
# <a name="procedure-overloading-visual-basic"></a><span data-ttu-id="8d111-102">Procedura přetížení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d111-102">Procedure Overloading (Visual Basic)</span></span>
<span data-ttu-id="8d111-103">*Přetížení* procedury znamená jeho definováním v několika verze, používá stejný název, ale seznamy různých parametrů.</span><span class="sxs-lookup"><span data-stu-id="8d111-103">*Overloading* a procedure means defining it in multiple versions, using the same name but different parameter lists.</span></span> <span data-ttu-id="8d111-104">Účelem přetížení je definovat několik úzce související verzí procedury bez nutnosti jejich odlišení podle názvu.</span><span class="sxs-lookup"><span data-stu-id="8d111-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span> <span data-ttu-id="8d111-105">To provedete pomocí různých seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="8d111-105">You do this by varying the parameter list.</span></span>  
  
## <a name="overloading-rules"></a><span data-ttu-id="8d111-106">Přetížení pravidla</span><span class="sxs-lookup"><span data-stu-id="8d111-106">Overloading Rules</span></span>  
 <span data-ttu-id="8d111-107">Pokud jste přetížení procedury, platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="8d111-107">When you overload a procedure, the following rules apply:</span></span>  
  
-   <span data-ttu-id="8d111-108">**Stejný název**.</span><span class="sxs-lookup"><span data-stu-id="8d111-108">**Same Name**.</span></span> <span data-ttu-id="8d111-109">Jednotlivé verze přetížené musí používat stejný název procedury.</span><span class="sxs-lookup"><span data-stu-id="8d111-109">Each overloaded version must use the same procedure name.</span></span>  
  
-   <span data-ttu-id="8d111-110">**Jiný podpis**.</span><span class="sxs-lookup"><span data-stu-id="8d111-110">**Different Signature**.</span></span> <span data-ttu-id="8d111-111">Každý přetížené verze se musí lišit od všech ostatních přetížené verzí alespoň v jedné z těchto ohledech:</span><span class="sxs-lookup"><span data-stu-id="8d111-111">Each overloaded version must differ from all other overloaded versions in at least one of the following respects:</span></span>  
  
    -   <span data-ttu-id="8d111-112">Počet parametrů</span><span class="sxs-lookup"><span data-stu-id="8d111-112">Number of parameters</span></span>  
  
    -   <span data-ttu-id="8d111-113">Pořadí parametrů</span><span class="sxs-lookup"><span data-stu-id="8d111-113">Order of the parameters</span></span>  
  
    -   <span data-ttu-id="8d111-114">Datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="8d111-114">Data types of the parameters</span></span>  
  
    -   <span data-ttu-id="8d111-115">Počet parametrů typu (pro obecný postup)</span><span class="sxs-lookup"><span data-stu-id="8d111-115">Number of type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="8d111-116">Návratový typ (pouze pro operátora převodu)</span><span class="sxs-lookup"><span data-stu-id="8d111-116">Return type (only for a conversion operator)</span></span>  
  
     <span data-ttu-id="8d111-117">Společně s název procedury předchozí položky se souhrnně označují jako *podpis* procedury.</span><span class="sxs-lookup"><span data-stu-id="8d111-117">Together with the procedure name, the preceding items are collectively called the *signature* of the procedure.</span></span> <span data-ttu-id="8d111-118">Při volání přetížené procedury kompilátor podpis používá ke kontrole, jestli volání správně odpovídá definici.</span><span class="sxs-lookup"><span data-stu-id="8d111-118">When you call an overloaded procedure, the compiler uses the signature to check that the call correctly matches the definition.</span></span>  
  
-   <span data-ttu-id="8d111-119">**Položky není součástí podpis**.</span><span class="sxs-lookup"><span data-stu-id="8d111-119">**Items Not Part of Signature**.</span></span> <span data-ttu-id="8d111-120">Bez různých podpis nelze přetížení procedury.</span><span class="sxs-lookup"><span data-stu-id="8d111-120">You cannot overload a procedure without varying the signature.</span></span> <span data-ttu-id="8d111-121">Nelze na konkrétní přetížení procedury pomocí různých pouze jeden nebo více z následujících položek:</span><span class="sxs-lookup"><span data-stu-id="8d111-121">In particular, you cannot overload a procedure by varying only one or more of the following items:</span></span>  
  
    -   <span data-ttu-id="8d111-122">Postup modifikátor klíčová slova, jako například `Public`, `Shared`, a `Static`</span><span class="sxs-lookup"><span data-stu-id="8d111-122">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>  
  
    -   <span data-ttu-id="8d111-123">Typ nebo parametr názvy parametrů</span><span class="sxs-lookup"><span data-stu-id="8d111-123">Parameter or type parameter names</span></span>  
  
    -   <span data-ttu-id="8d111-124">Zadejte parametr omezení (pro obecný postup)</span><span class="sxs-lookup"><span data-stu-id="8d111-124">Type parameter constraints (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="8d111-125">Klíčová slova – modifikátor parametrů, jako například `ByRef` a `Optional`</span><span class="sxs-lookup"><span data-stu-id="8d111-125">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>  
  
    -   <span data-ttu-id="8d111-126">Jestli vrátí hodnotu</span><span class="sxs-lookup"><span data-stu-id="8d111-126">Whether it returns a value</span></span>  
  
    -   <span data-ttu-id="8d111-127">datový typ vrácené hodnoty (s výjimkou operátora převodu)</span><span class="sxs-lookup"><span data-stu-id="8d111-127">The data type of the return value (except for a conversion operator)</span></span>  
  
     <span data-ttu-id="8d111-128">Položky v předchozím seznamu nejsou součástí podpis.</span><span class="sxs-lookup"><span data-stu-id="8d111-128">The items in the preceding list are not part of the signature.</span></span> <span data-ttu-id="8d111-129">I když je nemůžete použít k rozlišení mezi verzemi přetížené, můžete je lišit přetížené verze, které jsou rozlišené správně pomocí jejich podpisy.</span><span class="sxs-lookup"><span data-stu-id="8d111-129">Although you cannot use them to differentiate between overloaded versions, you can vary them among overloaded versions that are properly differentiated by their signatures.</span></span>  
  
-   <span data-ttu-id="8d111-130">**Pozdní vazba argumenty**.</span><span class="sxs-lookup"><span data-stu-id="8d111-130">**Late-Bound Arguments**.</span></span> <span data-ttu-id="8d111-131">Pokud máte v úmyslu proměnnou pozdní vázaný objekt předat přetížené verze, je potřeba deklarovat odpovídající parametr jako <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="8d111-131">If you intend to pass a late bound object variable to an overloaded version, you must declare the appropriate parameter as <xref:System.Object>.</span></span>  
  
## <a name="multiple-versions-of-a-procedure"></a><span data-ttu-id="8d111-132">Více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="8d111-132">Multiple Versions of a Procedure</span></span>  
 <span data-ttu-id="8d111-133">Předpokládejme, že jsou zápis `Sub` postup post transakce proti vyrovnávání zákazníka a chcete mít možnost k odkazování na Zákazník podle názvu nebo podle číslo účtu.</span><span class="sxs-lookup"><span data-stu-id="8d111-133">Suppose you are writing a `Sub` procedure to post a transaction against a customer's balance, and you want to be able to refer to the customer either by name or by account number.</span></span> <span data-ttu-id="8d111-134">K tomuto požadavku vyhovělo, můžete definovat dva různé `Sub` postupy, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8d111-134">To accommodate this, you can define two different `Sub` procedures, as in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#73](./codesnippet/VisualBasic/procedure-overloading_1.vb)]  
  
### <a name="overloaded-versions"></a><span data-ttu-id="8d111-135">Přetížené verze</span><span class="sxs-lookup"><span data-stu-id="8d111-135">Overloaded Versions</span></span>  
 <span data-ttu-id="8d111-136">Alternativou je přetížení název jedinou proceduru.</span><span class="sxs-lookup"><span data-stu-id="8d111-136">An alternative is to overload a single procedure name.</span></span> <span data-ttu-id="8d111-137">Můžete použít [přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md) – klíčové slovo na verzi postup pro každý seznam parametrů definujte takto:</span><span class="sxs-lookup"><span data-stu-id="8d111-137">You can use the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword to define a version of the procedure for each parameter list, as follows:</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/procedure-overloading_2.vb)]  
  
#### <a name="additional-overloads"></a><span data-ttu-id="8d111-138">Další přetížení</span><span class="sxs-lookup"><span data-stu-id="8d111-138">Additional Overloads</span></span>  
 <span data-ttu-id="8d111-139">Pokud jste chtěli také přijmout částka transakce buď `Decimal` nebo `Single`, může další přetížení `post` povolit pro tuto variantu.</span><span class="sxs-lookup"><span data-stu-id="8d111-139">If you also wanted to accept a transaction amount in either `Decimal` or `Single`, you could further overload `post` to allow for this variation.</span></span> <span data-ttu-id="8d111-140">Pokud jste to udělali to ke každému přetížení v předchozím příkladu byste měli čtyři `Sub` postupy, všechny se stejným názvem, ale s čtyři různé podpisy.</span><span class="sxs-lookup"><span data-stu-id="8d111-140">If you did this to each of the overloads in the preceding example, you would have four `Sub` procedures, all with the same name but with four different signatures.</span></span>  
  
## <a name="advantages-of-overloading"></a><span data-ttu-id="8d111-141">Výhody přetížení</span><span class="sxs-lookup"><span data-stu-id="8d111-141">Advantages of Overloading</span></span>  
 <span data-ttu-id="8d111-142">Výhodou přetížení procedury je v flexibilitu volání.</span><span class="sxs-lookup"><span data-stu-id="8d111-142">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="8d111-143">Použít `post` postup deklarované v předchozím příkladu volání kódu můžete získat Identifikace zákazníka jako buď `String` nebo `Integer`a pak zavolají stejným způsobem v obou případech.</span><span class="sxs-lookup"><span data-stu-id="8d111-143">To use the `post` procedure declared in the preceding example, the calling code can obtain the customer identification as either a `String` or an `Integer`, and then call the same procedure in either case.</span></span> <span data-ttu-id="8d111-144">Následující příklad ilustruje toto:</span><span class="sxs-lookup"><span data-stu-id="8d111-144">The following example illustrates this:</span></span>  
  
 [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/procedure-overloading_3.vb)]  
  
 [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/procedure-overloading_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8d111-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d111-145">See Also</span></span>  
 [<span data-ttu-id="8d111-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="8d111-146">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="8d111-147">Postupy: Definice více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="8d111-147">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="8d111-148">Postupy: Volání přetížené procedury</span><span class="sxs-lookup"><span data-stu-id="8d111-148">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="8d111-149">Postupy: Přetížení procedury, která přebírá nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="8d111-149">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="8d111-150">Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů</span><span class="sxs-lookup"><span data-stu-id="8d111-150">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="8d111-151">Aspekty přetížení procedur</span><span class="sxs-lookup"><span data-stu-id="8d111-151">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)  
 [<span data-ttu-id="8d111-152">Řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="8d111-152">Overload Resolution</span></span>](./overload-resolution.md)  
 [<span data-ttu-id="8d111-153">Overloads</span><span class="sxs-lookup"><span data-stu-id="8d111-153">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [<span data-ttu-id="8d111-154">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8d111-154">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
