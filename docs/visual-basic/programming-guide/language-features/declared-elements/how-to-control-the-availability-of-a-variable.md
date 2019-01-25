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
ms.openlocfilehash: 4d5db7fe474d8732e0ae37f3d95d0187eef68ec9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582485"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a><span data-ttu-id="cfda3-102">Postupy: Řízení dostupnosti proměnné (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cfda3-102">How to: Control the Availability of a Variable (Visual Basic)</span></span>
<span data-ttu-id="cfda3-103">Řízení dostupnosti proměnné tak, že zadáte jeho *úroveň přístupu*.</span><span class="sxs-lookup"><span data-stu-id="cfda3-103">You control the availability of a variable by specifying its *access level*.</span></span> <span data-ttu-id="cfda3-104">Úroveň přístupu určuje, jaký kód má oprávnění ke čtení nebo zápisu do proměnné.</span><span class="sxs-lookup"><span data-stu-id="cfda3-104">The access level determines what code has permission to read or write to the variable.</span></span>  
  
-   <span data-ttu-id="cfda3-105">*Členské proměnné* (definované na úrovni modulu a mimo všechny procedury) výchozí veřejný přístup, což znamená, že veškerý kód, který můžete vidět k nim přistupovat.</span><span class="sxs-lookup"><span data-stu-id="cfda3-105">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span></span> <span data-ttu-id="cfda3-106">Toto můžete změnit tak, že zadáte modifikátor přístupu.</span><span class="sxs-lookup"><span data-stu-id="cfda3-106">You can change this by specifying an access modifier.</span></span>  
  
-   <span data-ttu-id="cfda3-107">*Lokální proměnné* (definované uvnitř procedury) formálně mít veřejný přístup, i když k nim může přistupovat pouze kód v rámci jejich procedury.</span><span class="sxs-lookup"><span data-stu-id="cfda3-107">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span></span> <span data-ttu-id="cfda3-108">Nelze změnit úroveň přístupu lokální proměnné, ale můžete změnit úroveň přístupu postup, který jej obsahuje.</span><span class="sxs-lookup"><span data-stu-id="cfda3-108">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span></span>  
  
 <span data-ttu-id="cfda3-109">Další informace najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="cfda3-109">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="private-and-public-access"></a><span data-ttu-id="cfda3-110">Privátní a veřejné přístup</span><span class="sxs-lookup"><span data-stu-id="cfda3-110">Private and Public Access</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a><span data-ttu-id="cfda3-111">Aby byla proměnná přístupný pouze uvnitř jeho modulu, třídy nebo struktury</span><span class="sxs-lookup"><span data-stu-id="cfda3-111">To make a variable accessible only from within its module, class, or structure</span></span>  
  
1.  <span data-ttu-id="cfda3-112">Místo [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) proměnné v modulu, třídy nebo struktury, ale mimo všechny procedury.</span><span class="sxs-lookup"><span data-stu-id="cfda3-112">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="cfda3-113">Zahrnout [privátní](../../../../visual-basic/language-reference/modifiers/private.md) – klíčové slovo v `Dim` příkazu.</span><span class="sxs-lookup"><span data-stu-id="cfda3-113">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="cfda3-114">Může číst nebo zapisovat do proměnné z kamkoli v modulu, třídy nebo struktury, ale ne z mimo něj.</span><span class="sxs-lookup"><span data-stu-id="cfda3-114">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a><span data-ttu-id="cfda3-115">Aby byla proměnná přístupný z jakéhokoli kódu, který je můžou zobrazit</span><span class="sxs-lookup"><span data-stu-id="cfda3-115">To make a variable accessible from any code that can see it</span></span>  
  
1.  <span data-ttu-id="cfda3-116">Členské proměnné, umístěte `Dim` příkaz pro proměnné v modulu, třídy nebo struktury, ale mimo všechny procedury.</span><span class="sxs-lookup"><span data-stu-id="cfda3-116">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="cfda3-117">Zahrnout [veřejné](../../../../visual-basic/language-reference/modifiers/public.md) – klíčové slovo v `Dim` příkazu.</span><span class="sxs-lookup"><span data-stu-id="cfda3-117">Include the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="cfda3-118">Může číst nebo zapisovat do proměnné z veškerý kód, který spolupracuje s vaší sestavení.</span><span class="sxs-lookup"><span data-stu-id="cfda3-118">You can read or write to the variable from any code that interoperates with your assembly.</span></span>  
  
 <span data-ttu-id="cfda3-119">-nebo-</span><span class="sxs-lookup"><span data-stu-id="cfda3-119">-or-</span></span>  
  
1.  <span data-ttu-id="cfda3-120">Pro místní proměnné, umístěte `Dim` příkaz pro proměnnou uvnitř procedury.</span><span class="sxs-lookup"><span data-stu-id="cfda3-120">For a local variable, place the `Dim` statement for the variable inside a procedure.</span></span>  
  
2.  <span data-ttu-id="cfda3-121">Nejsou zahrnuté `Public` – klíčové slovo v `Dim` příkazu.</span><span class="sxs-lookup"><span data-stu-id="cfda3-121">Do not include the `Public` keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="cfda3-122">Může číst nebo zapisovat do proměnné z kdekoli v rámci procesu, ale ne z mimo něj.</span><span class="sxs-lookup"><span data-stu-id="cfda3-122">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span></span>  
  
## <a name="protected-and-friend-access"></a><span data-ttu-id="cfda3-123">Chráněné a přístup typu Friend</span><span class="sxs-lookup"><span data-stu-id="cfda3-123">Protected and Friend Access</span></span>  
 <span data-ttu-id="cfda3-124">Můžete omezit úroveň přístupu proměnné do své třídy a všechny odvozené třídy, nebo jeho sestavení.</span><span class="sxs-lookup"><span data-stu-id="cfda3-124">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span></span> <span data-ttu-id="cfda3-125">Můžete také zadat unii tato omezení, která umožňuje přístup z kódu v kterékoli odvozené třídě, nebo na jiném místě ve stejném sestavení.</span><span class="sxs-lookup"><span data-stu-id="cfda3-125">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span></span> <span data-ttu-id="cfda3-126">Zadejte tento sjednocení tím, že zkombinujete `Protected` a `Friend` klíčová slova ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="cfda3-126">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a><span data-ttu-id="cfda3-127">Aby byla proměnná přístupný pouze uvnitř své třídy a všechny odvozené třídy</span><span class="sxs-lookup"><span data-stu-id="cfda3-127">To make a variable accessible only from within its class and any derived classes</span></span>  
  
1.  <span data-ttu-id="cfda3-128">Místo `Dim` příkaz pro proměnnou uvnitř třídy, ale mimo všechny procedury.</span><span class="sxs-lookup"><span data-stu-id="cfda3-128">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="cfda3-129">Zahrnout [chráněné](../../../../visual-basic/language-reference/modifiers/protected.md) – klíčové slovo v `Dim` příkazu.</span><span class="sxs-lookup"><span data-stu-id="cfda3-129">Include the [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="cfda3-130">Může číst nebo zapisovat do proměnné z kdekoli v rámci třídy, stejně jako v rámci jakékoli třídy odvozené z něj, ale ne z mimo všechny třídy v řetězci odvození.</span><span class="sxs-lookup"><span data-stu-id="cfda3-130">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a><span data-ttu-id="cfda3-131">Aby byla proměnná přístupný pouze z v rámci stejného sestavení</span><span class="sxs-lookup"><span data-stu-id="cfda3-131">To make a variable accessible only from within the same assembly</span></span>  
  
1.  <span data-ttu-id="cfda3-132">Místo `Dim` příkaz pro proměnné v modulu, třídy nebo struktury, ale mimo všechny procedury.</span><span class="sxs-lookup"><span data-stu-id="cfda3-132">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="cfda3-133">Zahrnout [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) – klíčové slovo v `Dim` příkazu.</span><span class="sxs-lookup"><span data-stu-id="cfda3-133">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="cfda3-134">Může číst nebo zapisovat do proměnné z kamkoli v modulu, třídy nebo struktury, stejně jako v žádném kódu ve stejném sestavení, ale ne z mimo sestavení.</span><span class="sxs-lookup"><span data-stu-id="cfda3-134">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfda3-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="cfda3-135">Example</span></span>  
 <span data-ttu-id="cfda3-136">Následující příklad ukazuje deklarace proměnných s `Public`, `Protected`, `Friend`, `Protected Friend`, a `Private` úrovně přístupu.</span><span class="sxs-lookup"><span data-stu-id="cfda3-136">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span></span> <span data-ttu-id="cfda3-137">Všimněte si, že `Dim` příkaz určuje úroveň přístupu, není potřeba zahrnout `Dim` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="cfda3-137">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span></span>  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a><span data-ttu-id="cfda3-138">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cfda3-138">.NET Framework Security</span></span>  
 <span data-ttu-id="cfda3-139">Více omezující úroveň přístupu proměnné, čím menší pravděpodobnost, že škodlivý kód může být nesprávné využít.</span><span class="sxs-lookup"><span data-stu-id="cfda3-139">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfda3-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cfda3-140">See also</span></span>
- [<span data-ttu-id="cfda3-141">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cfda3-141">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="cfda3-142">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="cfda3-142">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="cfda3-143">Public</span><span class="sxs-lookup"><span data-stu-id="cfda3-143">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="cfda3-144">Protected</span><span class="sxs-lookup"><span data-stu-id="cfda3-144">Protected</span></span>](../../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="cfda3-145">Friend</span><span class="sxs-lookup"><span data-stu-id="cfda3-145">Friend</span></span>](../../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="cfda3-146">Private</span><span class="sxs-lookup"><span data-stu-id="cfda3-146">Private</span></span>](../../../../visual-basic/language-reference/modifiers/private.md)
