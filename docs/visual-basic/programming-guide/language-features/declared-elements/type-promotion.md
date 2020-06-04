---
title: Propagace typu
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
ms.openlocfilehash: 1e284b99a36cdf0f62aee2c45fd9f3bf544d1d81
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410705"
---
# <a name="type-promotion-visual-basic"></a><span data-ttu-id="7b0da-102">Propagace typu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b0da-102">Type Promotion (Visual Basic)</span></span>
<span data-ttu-id="7b0da-103">Při deklaraci programovacího prvku v modulu Visual Basic propaguje svůj rozsah na obor názvů obsahující modul.</span><span class="sxs-lookup"><span data-stu-id="7b0da-103">When you declare a programming element in a module, Visual Basic promotes its scope to the namespace containing the module.</span></span> <span data-ttu-id="7b0da-104">Tento postup se označuje jako *propagace typů*.</span><span class="sxs-lookup"><span data-stu-id="7b0da-104">This is known as *type promotion*.</span></span>  
  
 <span data-ttu-id="7b0da-105">Následující příklad ukazuje kostru definice modulu a dvou členů tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="7b0da-105">The following example shows a skeleton definition of a module and two members of that module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#1)]  
  
 <span data-ttu-id="7b0da-106">V rámci `projModule` jsou programovací prvky deklarované na úrovni modulu povýšeny na `projNamespace` .</span><span class="sxs-lookup"><span data-stu-id="7b0da-106">Within `projModule`, programming elements declared at module level are promoted to `projNamespace`.</span></span> <span data-ttu-id="7b0da-107">V předchozím příkladu `basicEnum` a `innerClass` je povýšen, ale není `numberSub` , protože není deklarována na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="7b0da-107">In the preceding example, `basicEnum` and `innerClass` are promoted, but `numberSub` is not, because it is not declared at module level.</span></span>  
  
## <a name="effect-of-type-promotion"></a><span data-ttu-id="7b0da-108">Účinek typu propagace</span><span class="sxs-lookup"><span data-stu-id="7b0da-108">Effect of Type Promotion</span></span>  
 <span data-ttu-id="7b0da-109">Účinek typu propagace je, že řetězec kvalifikace nemusí obsahovat název modulu.</span><span class="sxs-lookup"><span data-stu-id="7b0da-109">The effect of type promotion is that a qualification string does not need to include the module name.</span></span> <span data-ttu-id="7b0da-110">Následující příklad vytvoří dvě volání procedury v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7b0da-110">The following example makes two calls to the procedure in the preceding example.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#2)]  
  
 <span data-ttu-id="7b0da-111">V předchozím příkladu používá první volání kompletní řetězce kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="7b0da-111">In the preceding example, the first call uses complete qualification strings.</span></span> <span data-ttu-id="7b0da-112">To však není nutné z důvodu propagace typu.</span><span class="sxs-lookup"><span data-stu-id="7b0da-112">However, this is not necessary because of type promotion.</span></span> <span data-ttu-id="7b0da-113">Druhé volání přistupuje také ke členům modulu bez zahrnutí `projModule` do kvalifikačních řetězců.</span><span class="sxs-lookup"><span data-stu-id="7b0da-113">The second call also accesses the module's members without including `projModule` in the qualification strings.</span></span>  
  
## <a name="defeat-of-type-promotion"></a><span data-ttu-id="7b0da-114">Připraveno k povýšení typu</span><span class="sxs-lookup"><span data-stu-id="7b0da-114">Defeat of Type Promotion</span></span>  
 <span data-ttu-id="7b0da-115">Pokud obor názvů již obsahuje člena se stejným názvem jako s členem modulu, je pro tohoto člena modulu připraveno typ propagace.</span><span class="sxs-lookup"><span data-stu-id="7b0da-115">If the namespace already has a member with the same name as a module member, type promotion is defeated for that module member.</span></span> <span data-ttu-id="7b0da-116">Následující příklad znázorňuje kostru definice výčtu a modulu v rámci stejného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7b0da-116">The following example shows a skeleton definition of an enumeration and a module within the same namespace.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#3)]  
  
 <span data-ttu-id="7b0da-117">V předchozím příkladu Visual Basic nemůže propagovat třídu `abc` na, `thisNameSpace` protože již existuje výčet se stejným názvem na úrovni oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7b0da-117">In the preceding example, Visual Basic cannot promote class `abc` to `thisNameSpace` because there is already an enumeration with the same name at namespace level.</span></span> <span data-ttu-id="7b0da-118">Chcete-li získat přístup `abcSub` , je nutné použít plný kvalifikační řetězec `thisNamespace.thisModule.abc.abcSub` .</span><span class="sxs-lookup"><span data-stu-id="7b0da-118">To access `abcSub`, you must use the full qualification string `thisNamespace.thisModule.abc.abcSub`.</span></span> <span data-ttu-id="7b0da-119">Třída je však `xyz` stále povýšen a k nim můžete přistupovat `xyzSub` pomocí kratšího řetězce kvalifikace `thisNamespace.xyz.xyzSub` .</span><span class="sxs-lookup"><span data-stu-id="7b0da-119">However, class `xyz` is still promoted, and you can access `xyzSub` with the shorter qualification string `thisNamespace.xyz.xyzSub`.</span></span>  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a><span data-ttu-id="7b0da-120">Připravená propagace typu pro částečné typy</span><span class="sxs-lookup"><span data-stu-id="7b0da-120">Defeat of Type Promotion for Partial Types</span></span>  
 <span data-ttu-id="7b0da-121">Pokud třída nebo struktura uvnitř modulu používá klíčové slovo [Partial](../../../language-reference/modifiers/partial.md) , typ propagace je automaticky připraven pro tuto třídu nebo strukturu, bez ohledu na to, zda obor názvů obsahuje člena se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="7b0da-121">If a class or structure inside a module uses the [Partial](../../../language-reference/modifiers/partial.md) keyword, type promotion is automatically defeated for that class or structure, whether or not the namespace has a member with the same name.</span></span> <span data-ttu-id="7b0da-122">Další prvky v modulu jsou stále způsobilé pro povýšení typu.</span><span class="sxs-lookup"><span data-stu-id="7b0da-122">Other elements in the module are still eligible for type promotion.</span></span>  
  
 <span data-ttu-id="7b0da-123">**Výsledků.**</span><span class="sxs-lookup"><span data-stu-id="7b0da-123">**Consequences.**</span></span> <span data-ttu-id="7b0da-124">Připravená propagace typu částečné definice může způsobit neočekávané výsledky a dokonce i chyby kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="7b0da-124">Defeat of type promotion of a partial definition can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="7b0da-125">Následující příklad ukazuje kostru částečných definic třídy, z nichž jeden je uvnitř modulu.</span><span class="sxs-lookup"><span data-stu-id="7b0da-125">The following example shows skeleton partial definitions of a class, one of which is inside a module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#4)]  
  
 <span data-ttu-id="7b0da-126">V předchozím příkladu může vývojář očekávat, že kompilátor sloučí dvě částečné definice `sampleClass` .</span><span class="sxs-lookup"><span data-stu-id="7b0da-126">In the preceding example, the developer might expect the compiler to merge the two partial definitions of `sampleClass`.</span></span> <span data-ttu-id="7b0da-127">Kompilátor však nepovažuje povýšení na částečnou definici uvnitř `sampleModule` .</span><span class="sxs-lookup"><span data-stu-id="7b0da-127">However, the compiler does not consider promotion for the partial definition inside `sampleModule`.</span></span> <span data-ttu-id="7b0da-128">V důsledku toho se pokusí zkompilovat dvě samostatné a jedinečné třídy, jak s názvem, tak `sampleClass` s různými cestami kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="7b0da-128">As a result, it attempts to compile two separate and distinct classes, both named `sampleClass` but with different qualification paths.</span></span>  
  
 <span data-ttu-id="7b0da-129">Kompilátor sloučí částečné definice pouze v případě, že jsou jejich plně kvalifikované cesty identické.</span><span class="sxs-lookup"><span data-stu-id="7b0da-129">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="7b0da-130">Doporučení</span><span class="sxs-lookup"><span data-stu-id="7b0da-130">Recommendations</span></span>  
 <span data-ttu-id="7b0da-131">Následující doporučení reprezentují dobrý postup programování.</span><span class="sxs-lookup"><span data-stu-id="7b0da-131">The following recommendations represent good programming practice.</span></span>  
  
- <span data-ttu-id="7b0da-132">**Jedinečné názvy.**</span><span class="sxs-lookup"><span data-stu-id="7b0da-132">**Unique Names.**</span></span> <span data-ttu-id="7b0da-133">Pokud máte plnou kontrolu nad pojmenování programovacích prvků, je vždy vhodné použít jedinečné názvy všude.</span><span class="sxs-lookup"><span data-stu-id="7b0da-133">When you have full control over the naming of programming elements, it is always a good idea to use unique names everywhere.</span></span> <span data-ttu-id="7b0da-134">Identické názvy vyžadují dodatečnou kvalifikaci a je možné, že váš kód bude obtížnější číst.</span><span class="sxs-lookup"><span data-stu-id="7b0da-134">Identical names require extra qualification and can make your code harder to read.</span></span> <span data-ttu-id="7b0da-135">Můžou také vést k drobným chybám a neočekávaným výsledkům.</span><span class="sxs-lookup"><span data-stu-id="7b0da-135">They can also lead to subtle errors and unexpected results.</span></span>  
  
- <span data-ttu-id="7b0da-136">**Úplná kvalifikace.**</span><span class="sxs-lookup"><span data-stu-id="7b0da-136">**Full Qualification.**</span></span> <span data-ttu-id="7b0da-137">Při práci s moduly a dalšími prvky ve stejném oboru názvů je nejbezpečnější přístup vždy používat úplnou kvalifikaci pro všechny programovací prvky.</span><span class="sxs-lookup"><span data-stu-id="7b0da-137">When you are working with modules and other elements in the same namespace, the safest approach is to always use full qualification for all programming elements.</span></span> <span data-ttu-id="7b0da-138">Pokud je u člena modulu připraveno propagace typu a nejste plně kvalifikováni tohoto člena, mohli byste neúmyslně přistupovat k jinému programovacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="7b0da-138">If type promotion is defeated for a module member and you do not fully qualify that member, you could inadvertently access a different programming element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b0da-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b0da-139">See also</span></span>

- [<span data-ttu-id="7b0da-140">Module – příkaz</span><span class="sxs-lookup"><span data-stu-id="7b0da-140">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="7b0da-141">Namespace – příkaz</span><span class="sxs-lookup"><span data-stu-id="7b0da-141">Namespace Statement</span></span>](../../../language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="7b0da-142">Částečné</span><span class="sxs-lookup"><span data-stu-id="7b0da-142">Partial</span></span>](../../../language-reference/modifiers/partial.md)
- [<span data-ttu-id="7b0da-143">Rozsah v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7b0da-143">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="7b0da-144">Postupy: Řízení rozsahu proměnné</span><span class="sxs-lookup"><span data-stu-id="7b0da-144">How to: Control the Scope of a Variable</span></span>](how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="7b0da-145">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="7b0da-145">References to Declared Elements</span></span>](references-to-declared-elements.md)
