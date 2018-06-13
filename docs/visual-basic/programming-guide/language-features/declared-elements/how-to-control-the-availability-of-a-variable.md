---
title: 'Postupy: Řízení dostupnosti proměnné (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
ms.openlocfilehash: 27ee5d3405ea24c0754cffa85e9b89b2ac561e42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652165"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a><span data-ttu-id="21910-102">Postupy: Řízení dostupnosti proměnné (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21910-102">How to: Control the Availability of a Variable (Visual Basic)</span></span>
<span data-ttu-id="21910-103">Řízení dostupnosti proměnné zadáním jeho *úroveň přístupu*.</span><span class="sxs-lookup"><span data-stu-id="21910-103">You control the availability of a variable by specifying its *access level*.</span></span> <span data-ttu-id="21910-104">Úroveň přístupu určuje, jaký kód má oprávnění ke čtení nebo zápisu do proměnné.</span><span class="sxs-lookup"><span data-stu-id="21910-104">The access level determines what code has permission to read or write to the variable.</span></span>  
  
-   <span data-ttu-id="21910-105">*Členské proměnné* (definovanou na úrovni modulu a mimo libovolná procedura) výchozí nastavení veřejný přístup, což znamená, kód, který můžete vidět k nim mají přístup.</span><span class="sxs-lookup"><span data-stu-id="21910-105">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span></span> <span data-ttu-id="21910-106">Toto můžete změnit zadáním – modifikátor přístupu.</span><span class="sxs-lookup"><span data-stu-id="21910-106">You can change this by specifying an access modifier.</span></span>  
  
-   <span data-ttu-id="21910-107">*Lokální proměnné* (definované uvnitř procedury) jmenovitě mít veřejný přístup, i když k nim mít přístup jenom kód v rámci jejich procedury.</span><span class="sxs-lookup"><span data-stu-id="21910-107">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span></span> <span data-ttu-id="21910-108">Nelze změnit úroveň přístupu, místní proměnné, ale můžete změnit úroveň přístupu tohoto postupu, který jej obsahuje.</span><span class="sxs-lookup"><span data-stu-id="21910-108">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span></span>  
  
 <span data-ttu-id="21910-109">Další informace najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="21910-109">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="private-and-public-access"></a><span data-ttu-id="21910-110">Privátní a veřejné přístup</span><span class="sxs-lookup"><span data-stu-id="21910-110">Private and Public Access</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a><span data-ttu-id="21910-111">Chcete-li proměnnou přístupné pouze v rámci jeho modulu, třídu nebo strukturu</span><span class="sxs-lookup"><span data-stu-id="21910-111">To make a variable accessible only from within its module, class, or structure</span></span>  
  
1.  <span data-ttu-id="21910-112">Místo [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md) pro proměnnou uvnitř modulu, třídu nebo strukturu, ale mimo jakéhokoli postupu.</span><span class="sxs-lookup"><span data-stu-id="21910-112">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="21910-113">Zahrnout [privátní](../../../../visual-basic/language-reference/modifiers/private.md) – klíčové slovo v `Dim` příkaz.</span><span class="sxs-lookup"><span data-stu-id="21910-113">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="21910-114">Můžou číst nebo zapisovat do proměnné z kamkoli v modulu, třídu nebo strukturu, ale nikoli z mimo něj.</span><span class="sxs-lookup"><span data-stu-id="21910-114">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a><span data-ttu-id="21910-115">Chcete-li proměnnou přístupné z kód, který můžete zobrazit</span><span class="sxs-lookup"><span data-stu-id="21910-115">To make a variable accessible from any code that can see it</span></span>  
  
1.  <span data-ttu-id="21910-116">Členské proměnné, umístěte `Dim` příkaz pro proměnnou uvnitř modulu, třídu nebo strukturu, ale mimo jakéhokoli postupu.</span><span class="sxs-lookup"><span data-stu-id="21910-116">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="21910-117">Zahrnout [veřejné](../../../../visual-basic/language-reference/modifiers/public.md) – klíčové slovo v `Dim` příkaz.</span><span class="sxs-lookup"><span data-stu-id="21910-117">Include the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="21910-118">Můžou číst nebo zapisovat do proměnné ze kód, který bude spolupracovat s vaší sestavení.</span><span class="sxs-lookup"><span data-stu-id="21910-118">You can read or write to the variable from any code that interoperates with your assembly.</span></span>  
  
 <span data-ttu-id="21910-119">-nebo-</span><span class="sxs-lookup"><span data-stu-id="21910-119">-or-</span></span>  
  
1.  <span data-ttu-id="21910-120">Pro místní proměnné, umístěte `Dim` příkaz pro proměnnou uvnitř procedury.</span><span class="sxs-lookup"><span data-stu-id="21910-120">For a local variable, place the `Dim` statement for the variable inside a procedure.</span></span>  
  
2.  <span data-ttu-id="21910-121">Nezahrnovat `Public` – klíčové slovo v `Dim` příkaz.</span><span class="sxs-lookup"><span data-stu-id="21910-121">Do not include the `Public` keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="21910-122">Můžou číst nebo zapisovat do proměnné z kdekoli v rámci procesu, ale nikoli z mimo něj.</span><span class="sxs-lookup"><span data-stu-id="21910-122">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span></span>  
  
## <a name="protected-and-friend-access"></a><span data-ttu-id="21910-123">Protected Friend přístupu a</span><span class="sxs-lookup"><span data-stu-id="21910-123">Protected and Friend Access</span></span>  
 <span data-ttu-id="21910-124">Můžete omezit úroveň přístupu proměnné do své třídy a všechny odvozené třídy, nebo jeho sestavení.</span><span class="sxs-lookup"><span data-stu-id="21910-124">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span></span> <span data-ttu-id="21910-125">Můžete také zadat sjednocení tato omezení, která umožňuje přístup z kódu všechny odvozené třídy nebo na jiném místě ve stejném sestavení.</span><span class="sxs-lookup"><span data-stu-id="21910-125">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span></span> <span data-ttu-id="21910-126">Zadejte tento sjednocení tím, že zkombinujete `Protected` a `Friend` klíčová slova ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="21910-126">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a><span data-ttu-id="21910-127">Chcete-li proměnnou přístupné pouze v rámci své třídy a všechny odvozené třídy</span><span class="sxs-lookup"><span data-stu-id="21910-127">To make a variable accessible only from within its class and any derived classes</span></span>  
  
1.  <span data-ttu-id="21910-128">Místo `Dim` příkaz pro proměnnou uvnitř třídy, ale mimo jakéhokoli postupu.</span><span class="sxs-lookup"><span data-stu-id="21910-128">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="21910-129">Zahrnout [chráněné](../../../../visual-basic/language-reference/modifiers/protected.md) – klíčové slovo v `Dim` příkaz.</span><span class="sxs-lookup"><span data-stu-id="21910-129">Include the [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="21910-130">Můžou číst nebo zapisovat do proměnné z kdekoli v rámci třídy, ale také v libovolné třídy odvozené z něj, ale nikoli z mimo všechny třídy v řetězu odvození.</span><span class="sxs-lookup"><span data-stu-id="21910-130">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a><span data-ttu-id="21910-131">Chcete-li proměnnou přístupné pouze v rámci stejného sestavení</span><span class="sxs-lookup"><span data-stu-id="21910-131">To make a variable accessible only from within the same assembly</span></span>  
  
1.  <span data-ttu-id="21910-132">Místo `Dim` příkaz pro proměnnou uvnitř modulu, třídu nebo strukturu, ale mimo jakéhokoli postupu.</span><span class="sxs-lookup"><span data-stu-id="21910-132">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="21910-133">Zahrnout [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) – klíčové slovo v `Dim` příkaz.</span><span class="sxs-lookup"><span data-stu-id="21910-133">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="21910-134">Můžou číst nebo zapisovat do proměnné z kamkoli v modulu, třídu nebo strukturu, a také z jakékoli kódu ve stejném sestavení, ale nikoli z mimo sestavení.</span><span class="sxs-lookup"><span data-stu-id="21910-134">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21910-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="21910-135">Example</span></span>  
 <span data-ttu-id="21910-136">Následující příklad ukazuje deklarace proměnné s `Public`, `Protected`, `Friend`, `Protected Friend`, a `Private` úrovně přístupu.</span><span class="sxs-lookup"><span data-stu-id="21910-136">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span></span> <span data-ttu-id="21910-137">Všimněte si, že pokud `Dim` příkaz určuje úroveň přístupu, není potřeba zahrnovat `Dim` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="21910-137">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span></span>  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a><span data-ttu-id="21910-138">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="21910-138">.NET Framework Security</span></span>  
 <span data-ttu-id="21910-139">Více omezující úroveň přístupu proměnné, tím menší pravděpodobnost, že škodlivý kód způsobit nesprávné použití ho.</span><span class="sxs-lookup"><span data-stu-id="21910-139">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21910-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="21910-140">See Also</span></span>  
 [<span data-ttu-id="21910-141">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="21910-141">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="21910-142">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="21910-142">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="21910-143">Public</span><span class="sxs-lookup"><span data-stu-id="21910-143">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="21910-144">Protected</span><span class="sxs-lookup"><span data-stu-id="21910-144">Protected</span></span>](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="21910-145">Friend</span><span class="sxs-lookup"><span data-stu-id="21910-145">Friend</span></span>](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="21910-146">Private</span><span class="sxs-lookup"><span data-stu-id="21910-146">Private</span></span>](../../../../visual-basic/language-reference/modifiers/private.md)
