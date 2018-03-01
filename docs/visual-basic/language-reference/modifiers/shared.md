---
title: Shared (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fce13c308a449e63eacc2bc4c94c274c7e25506a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="shared-visual-basic"></a><span data-ttu-id="4018b-102">Shared (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4018b-102">Shared (Visual Basic)</span></span>
<span data-ttu-id="4018b-103">Určuje, že jeden nebo více deklarované programovací elementy jsou spojeny s třídu nebo strukturu ve velkém a ne s konkrétní instanci třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="4018b-103">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4018b-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4018b-104">Remarks</span></span>  
  
## <a name="when-to-use-shared"></a><span data-ttu-id="4018b-105">Kdy použít sdílené</span><span class="sxs-lookup"><span data-stu-id="4018b-105">When to Use Shared</span></span>  
 <span data-ttu-id="4018b-106">Sdílení členem třídu nebo strukturu je k dispozici pro všechny instance, místo *sdíleném*, kde každá instance zachová vlastní kopie.</span><span class="sxs-lookup"><span data-stu-id="4018b-106">Sharing a member of a class or structure makes it available to every instance, rather than *nonshared*, where each instance keeps its own copy.</span></span> <span data-ttu-id="4018b-107">To je užitečné, například pokud hodnota proměnné platí v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4018b-107">This is useful, for example, if the value of a variable applies to the entire application.</span></span> <span data-ttu-id="4018b-108">Pokud je deklarovat tuto proměnnou na `Shared`, pak všechny instance přístup k stejné umístění úložiště, a pokud se jedna instance se změní hodnota proměnné, všechny instance k aktualizované hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4018b-108">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span></span>  
  
 <span data-ttu-id="4018b-109">Sdílení nezmění úroveň přístupu tohoto člena.</span><span class="sxs-lookup"><span data-stu-id="4018b-109">Sharing does not alter the access level of a member.</span></span> <span data-ttu-id="4018b-110">Například je možné sdílet člena třídy a privátní (k dispozici pouze z v rámci třídy), nebo sdíleném a veřejné.</span><span class="sxs-lookup"><span data-stu-id="4018b-110">For example, a class member can be shared and private (accessible only from within the class), or nonshared and public.</span></span> <span data-ttu-id="4018b-111">Další informace najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="4018b-111">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="4018b-112">Pravidla</span><span class="sxs-lookup"><span data-stu-id="4018b-112">Rules</span></span>  
  
-   <span data-ttu-id="4018b-113">**Kontext deklarace.**</span><span class="sxs-lookup"><span data-stu-id="4018b-113">**Declaration Context.**</span></span> <span data-ttu-id="4018b-114">Můžete použít `Shared` jenom na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="4018b-114">You can use `Shared` only at module level.</span></span> <span data-ttu-id="4018b-115">To znamená kontext deklarace `Shared` element musí být třídu nebo strukturu a nemůže být zdrojový soubor, obor názvů nebo postupu.</span><span class="sxs-lookup"><span data-stu-id="4018b-115">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span></span>  
  
-   <span data-ttu-id="4018b-116">**Kombinovaná parametrů.**</span><span class="sxs-lookup"><span data-stu-id="4018b-116">**Combined Modifiers.**</span></span> <span data-ttu-id="4018b-117">Nelze zadat `Shared` společně s [přepsání](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), nebo [ Statické](../../../visual-basic/language-reference/modifiers/static.md) ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="4018b-117">You cannot specify `Shared` together with [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), or [Static](../../../visual-basic/language-reference/modifiers/static.md) in the same declaration.</span></span>  
  
-   <span data-ttu-id="4018b-118">**Přístup k.**</span><span class="sxs-lookup"><span data-stu-id="4018b-118">**Accessing.**</span></span> <span data-ttu-id="4018b-119">Můžete zobrazit sdílené element kvalifikující ho s názvem třídu nebo strukturu, ne při název proměnné konkrétní instanci jeho třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="4018b-119">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span></span> <span data-ttu-id="4018b-120">I nemáte k vytvoření instance třídu nebo strukturu pro přístup k jeho sdílení členové.</span><span class="sxs-lookup"><span data-stu-id="4018b-120">You do not even have to create an instance of a class or structure to access its shared members.</span></span>  
  
     <span data-ttu-id="4018b-121">V následujícím příkladu volání sdílený postup <xref:System.Double.IsNaN%2A> vystavené <xref:System.Double> struktura.</span><span class="sxs-lookup"><span data-stu-id="4018b-121">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span></span>  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   <span data-ttu-id="4018b-122">**Implicitní sdílení.**</span><span class="sxs-lookup"><span data-stu-id="4018b-122">**Implicit Sharing.**</span></span> <span data-ttu-id="4018b-123">Nelze použít `Shared` modifikátor v [příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md), ale konstanty implicitně sdílejí.</span><span class="sxs-lookup"><span data-stu-id="4018b-123">You cannot use the `Shared` modifier in a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md), but constants are implicitly shared.</span></span> <span data-ttu-id="4018b-124">Podobně nelze deklarovat být členem skupiny modulu nebo rozhraní `Shared`, ale jsou implicitně sdílené.</span><span class="sxs-lookup"><span data-stu-id="4018b-124">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="4018b-125">Chování</span><span class="sxs-lookup"><span data-stu-id="4018b-125">Behavior</span></span>  
  
-   <span data-ttu-id="4018b-126">**Úložiště.**</span><span class="sxs-lookup"><span data-stu-id="4018b-126">**Storage.**</span></span> <span data-ttu-id="4018b-127">Sdílené proměnné nebo událostí je uložené v paměti pouze po, bez ohledu na to, kolik nebo několik instancí vytvoření z jeho třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="4018b-127">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span></span> <span data-ttu-id="4018b-128">Podobně sdílený postup nebo vlastnost obsahuje pouze jednu sadu lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="4018b-128">Similarly, a shared procedure or property holds only one set of local variables.</span></span>  
  
-   <span data-ttu-id="4018b-129">**Přístup k prostřednictvím proměnnou Instance.**</span><span class="sxs-lookup"><span data-stu-id="4018b-129">**Accessing through an Instance Variable.**</span></span> <span data-ttu-id="4018b-130">Je možné získat přístup k prvku sdílené s kvalifikující s názvem proměnné, která obsahuje konkrétní instanci jeho třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="4018b-130">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span></span> <span data-ttu-id="4018b-131">I když tento postup obvykle funguje podle očekávání, kompilátor vygeneruje upozornění a umožňuje přístup pomocí názvu třídu nebo strukturu místo proměnnou.</span><span class="sxs-lookup"><span data-stu-id="4018b-131">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span></span>  
  
-   <span data-ttu-id="4018b-132">**Přístup k prostřednictvím výrazu Instance.**</span><span class="sxs-lookup"><span data-stu-id="4018b-132">**Accessing through an Instance Expression.**</span></span> <span data-ttu-id="4018b-133">Pokud máte přístup k prvku sdílené prostřednictvím výraz, který vrací instanci třídy jeho třídu nebo strukturu, kompilátor umožňuje přístup pomocí názvu třídu nebo strukturu místo hodnocení výrazu.</span><span class="sxs-lookup"><span data-stu-id="4018b-133">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span></span> <span data-ttu-id="4018b-134">To poskytuje neočekávané výsledky, pokud má výraz, který se provádět další akce, jakož i vrací instanci.</span><span class="sxs-lookup"><span data-stu-id="4018b-134">This produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span></span> <span data-ttu-id="4018b-135">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="4018b-135">The following example illustrates this.</span></span>  
  
    ```  
    Sub main()  
        shareTotal.total = 10  
        ' The preceding line is the preferred way to access total.  
        Dim instanceVar As New shareTotal  
        instanceVar.total += 100  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of through  
        ' the variable instanceVar. This works as expected and adds  
        ' 100 to total.  
        returnClass().total += 1000  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of calling  
        ' returnClass(). This adds 1000 to total but does not work as  
        ' expected, because the MsgBox in returnClass() does not run.  
        MsgBox("Value of total is " & CStr(shareTotal.total))  
    End Sub  
    Public Function returnClass() As shareTotal  
        MsgBox("Function returnClass() called")  
        Return New shareTotal  
    End Function  
    Public Class shareTotal  
        Public Shared total As Integer  
    End Class  
    ```  
  
     <span data-ttu-id="4018b-136">V předchozím příkladu, kompilátor vygeneruje upozornění obou časy kód přistupuje k sdílené proměnné `total` prostřednictvím instance.</span><span class="sxs-lookup"><span data-stu-id="4018b-136">In the preceding example, the compiler generates a warning message both times the code accesses the shared variable `total` through an instance.</span></span> <span data-ttu-id="4018b-137">V každém případě umožňuje přístup přímo prostřednictvím třídy `shareTotal` a zajistěte, aby nebyly používat všechny instance.</span><span class="sxs-lookup"><span data-stu-id="4018b-137">In each case it makes the access directly through the class `shareTotal` and does not make use of any instance.</span></span> <span data-ttu-id="4018b-138">V případě určený volání postup `returnClass`, to znamená i negeneruje volání `returnClass`, takže není provést další akce zobrazení "Funkce returnClass() názvem".</span><span class="sxs-lookup"><span data-stu-id="4018b-138">In the case of the intended call to the procedure `returnClass`, this means it does not even generate a call to `returnClass`, so the additional action of displaying "Function returnClass() called" is not performed.</span></span>  
  
 <span data-ttu-id="4018b-139">`Shared` Modifikátor lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="4018b-139">The `Shared` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="4018b-140">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="4018b-140">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="4018b-141">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="4018b-141">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="4018b-142">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="4018b-142">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="4018b-143">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="4018b-143">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="4018b-144">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="4018b-144">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="4018b-145">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="4018b-145">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="4018b-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="4018b-146">See Also</span></span>  
 [<span data-ttu-id="4018b-147">Stínů</span><span class="sxs-lookup"><span data-stu-id="4018b-147">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="4018b-148">Statické</span><span class="sxs-lookup"><span data-stu-id="4018b-148">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)  
 [<span data-ttu-id="4018b-149">Doba platnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4018b-149">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="4018b-150">Postupy</span><span class="sxs-lookup"><span data-stu-id="4018b-150">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="4018b-151">Struktury</span><span class="sxs-lookup"><span data-stu-id="4018b-151">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="4018b-152">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="4018b-152">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
