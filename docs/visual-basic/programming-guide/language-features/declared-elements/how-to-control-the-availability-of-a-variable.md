---
title: 'Postupy: Řízení dostupnosti proměnné'
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
ms.openlocfilehash: 886b57909cf6ba25dbaceea5c5f06eb4e3ba6f1f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345391"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a><span data-ttu-id="e2994-102">Postupy: Řízení dostupnosti proměnné (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2994-102">How to: Control the Availability of a Variable (Visual Basic)</span></span>
<span data-ttu-id="e2994-103">Dostupnost proměnné můžete řídit zadáním její *úrovně přístupu*.</span><span class="sxs-lookup"><span data-stu-id="e2994-103">You control the availability of a variable by specifying its *access level*.</span></span> <span data-ttu-id="e2994-104">Úroveň přístupu určuje, který kód má oprávnění ke čtení nebo zápisu do proměnné.</span><span class="sxs-lookup"><span data-stu-id="e2994-104">The access level determines what code has permission to read or write to the variable.</span></span>  
  
- <span data-ttu-id="e2994-105">*Členské proměnné* (definované na úrovni modulu a mimo jakoukoli proceduru) jsou výchozí pro veřejný přístup, což znamená, že k nim budou mít přístup všechny kódy, které je můžou zobrazit.</span><span class="sxs-lookup"><span data-stu-id="e2994-105">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span></span> <span data-ttu-id="e2994-106">To můžete změnit zadáním modifikátoru přístupu.</span><span class="sxs-lookup"><span data-stu-id="e2994-106">You can change this by specifying an access modifier.</span></span>  
  
- <span data-ttu-id="e2994-107">*Místní proměnné* (definované uvnitř procedury) mají formálně přístupný veřejný přístup, i když k nim mají přístup jenom kód v rámci jejich postupu.</span><span class="sxs-lookup"><span data-stu-id="e2994-107">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span></span> <span data-ttu-id="e2994-108">Úroveň přístupu místní proměnné se nedá změnit, ale můžete změnit úroveň přístupu pro proceduru, která ho obsahuje.</span><span class="sxs-lookup"><span data-stu-id="e2994-108">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span></span>  
  
 <span data-ttu-id="e2994-109">Další informace najdete v tématu [úrovně přístupu v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="e2994-109">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="private-and-public-access"></a><span data-ttu-id="e2994-110">Privátní a veřejný přístup</span><span class="sxs-lookup"><span data-stu-id="e2994-110">Private and Public Access</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a><span data-ttu-id="e2994-111">Aby byla proměnná přístupná pouze v rámci svého modulu, třídy nebo struktury</span><span class="sxs-lookup"><span data-stu-id="e2994-111">To make a variable accessible only from within its module, class, or structure</span></span>  
  
1. <span data-ttu-id="e2994-112">Do modulu, třídy nebo struktury umístěte [příkaz Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) pro proměnnou, ale mimo jakoukoli proceduru.</span><span class="sxs-lookup"><span data-stu-id="e2994-112">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="e2994-113">Do příkazu `Dim` zahrňte klíčové slovo [Private](../../../../visual-basic/language-reference/modifiers/private.md) .</span><span class="sxs-lookup"><span data-stu-id="e2994-113">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="e2994-114">Můžete číst nebo zapisovat do proměnné odkudkoli v rámci modulu, třídy nebo struktury, ale ne z vnějšku.</span><span class="sxs-lookup"><span data-stu-id="e2994-114">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a><span data-ttu-id="e2994-115">Aby byla proměnná přístupná z libovolného kódu, který je uvidí</span><span class="sxs-lookup"><span data-stu-id="e2994-115">To make a variable accessible from any code that can see it</span></span>  
  
1. <span data-ttu-id="e2994-116">Pro členskou proměnnou umístěte příkaz `Dim` pro proměnnou uvnitř modulu, třídy nebo struktury, ale vně jakékoli procedury.</span><span class="sxs-lookup"><span data-stu-id="e2994-116">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="e2994-117">Do příkazu `Dim` zahrňte klíčové slovo [Public](../../../../visual-basic/language-reference/modifiers/public.md) .</span><span class="sxs-lookup"><span data-stu-id="e2994-117">Include the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="e2994-118">Můžete číst nebo zapisovat do proměnné z libovolného kódu, který spolupracuje s vaším sestavením.</span><span class="sxs-lookup"><span data-stu-id="e2994-118">You can read or write to the variable from any code that interoperates with your assembly.</span></span>  
  
 <span data-ttu-id="e2994-119">-nebo-</span><span class="sxs-lookup"><span data-stu-id="e2994-119">-or-</span></span>  
  
1. <span data-ttu-id="e2994-120">Pro místní proměnnou umístěte příkaz `Dim` pro proměnnou uvnitř procedury.</span><span class="sxs-lookup"><span data-stu-id="e2994-120">For a local variable, place the `Dim` statement for the variable inside a procedure.</span></span>  
  
2. <span data-ttu-id="e2994-121">Nezahrnujte klíčové slovo `Public` do příkazu `Dim`.</span><span class="sxs-lookup"><span data-stu-id="e2994-121">Do not include the `Public` keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="e2994-122">Můžete číst nebo zapisovat do proměnné z libovolného místa v rámci tohoto postupu, ale ne z vnějšku.</span><span class="sxs-lookup"><span data-stu-id="e2994-122">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span></span>  
  
## <a name="protected-and-friend-access"></a><span data-ttu-id="e2994-123">Chráněný a přítel přístup</span><span class="sxs-lookup"><span data-stu-id="e2994-123">Protected and Friend Access</span></span>  
 <span data-ttu-id="e2994-124">Úroveň přístupu proměnné lze omezit na její třídu a jakékoli odvozené třídy nebo na její sestavení.</span><span class="sxs-lookup"><span data-stu-id="e2994-124">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span></span> <span data-ttu-id="e2994-125">Můžete také zadat sjednocení těchto omezení, což umožňuje přístup z kódu v jakékoli odvozené třídě nebo na jakémkoli jiném místě ve stejném sestavení.</span><span class="sxs-lookup"><span data-stu-id="e2994-125">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span></span> <span data-ttu-id="e2994-126">Tuto sjednocení zadáte kombinováním klíčových slov `Protected` a `Friend` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="e2994-126">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a><span data-ttu-id="e2994-127">Chcete-li zpřístupnit proměnnou pouze v rámci své třídy a všech odvozených tříd</span><span class="sxs-lookup"><span data-stu-id="e2994-127">To make a variable accessible only from within its class and any derived classes</span></span>  
  
1. <span data-ttu-id="e2994-128">Umístěte příkaz `Dim` pro proměnnou uvnitř třídy, ale vně jakékoli procedury.</span><span class="sxs-lookup"><span data-stu-id="e2994-128">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="e2994-129">Do příkazu `Dim` zahrňte klíčové slovo [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) .</span><span class="sxs-lookup"><span data-stu-id="e2994-129">Include the [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="e2994-130">Můžete číst nebo zapisovat do proměnné odkudkoli v rámci třídy a také z jakékoli třídy odvozené z ní, ale ne z vnějšku žádné třídy v řetězu odvození.</span><span class="sxs-lookup"><span data-stu-id="e2994-130">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a><span data-ttu-id="e2994-131">Chcete-li nastavit přístup k proměnné pouze v rámci stejného sestavení</span><span class="sxs-lookup"><span data-stu-id="e2994-131">To make a variable accessible only from within the same assembly</span></span>  
  
1. <span data-ttu-id="e2994-132">Umístěte příkaz `Dim` pro proměnnou uvnitř modulu, třídy nebo struktury, ale vně jakékoli procedury.</span><span class="sxs-lookup"><span data-stu-id="e2994-132">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="e2994-133">Do příkazu `Dim` zahrňte klíčové slovo [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) .</span><span class="sxs-lookup"><span data-stu-id="e2994-133">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="e2994-134">Můžete číst nebo zapisovat do proměnné odkudkoli v rámci modulu, třídy nebo struktury, jakož i z libovolného kódu ve stejném sestavení, ale nikoli mimo sestavení.</span><span class="sxs-lookup"><span data-stu-id="e2994-134">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2994-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="e2994-135">Example</span></span>  
 <span data-ttu-id="e2994-136">Následující příklad ukazuje deklarace proměnných s úrovněmi přístupu `Public`, `Protected`, `Friend`, `Protected Friend`a `Private`.</span><span class="sxs-lookup"><span data-stu-id="e2994-136">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span></span> <span data-ttu-id="e2994-137">Všimněte si, že když příkaz `Dim` určuje úroveň přístupu, nemusíte zahrnovat klíčové slovo `Dim`.</span><span class="sxs-lookup"><span data-stu-id="e2994-137">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span></span>  
  
```vb  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a><span data-ttu-id="e2994-138">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e2994-138">.NET Framework Security</span></span>  
 <span data-ttu-id="e2994-139">Přísnější úroveň přístupu proměnné, menší riziko, že škodlivý kód může nevhodným způsobem používat.</span><span class="sxs-lookup"><span data-stu-id="e2994-139">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2994-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2994-140">See also</span></span>

- [<span data-ttu-id="e2994-141">Úrovně přístupu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e2994-141">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="e2994-142">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="e2994-142">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="e2994-143">Public</span><span class="sxs-lookup"><span data-stu-id="e2994-143">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="e2994-144">Protected</span><span class="sxs-lookup"><span data-stu-id="e2994-144">Protected</span></span>](../../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="e2994-145">Friend</span><span class="sxs-lookup"><span data-stu-id="e2994-145">Friend</span></span>](../../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="e2994-146">Private</span><span class="sxs-lookup"><span data-stu-id="e2994-146">Private</span></span>](../../../../visual-basic/language-reference/modifiers/private.md)
