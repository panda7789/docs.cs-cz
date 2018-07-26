---
title: Shared (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: b76d999bfe3f7ae5205cb9486e040c1d6191b78c
ms.sourcegitcommit: dc02d7d95f1e3efcc7166eaf431b0ec0dc9d8dca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37143528"
---
# <a name="shared-visual-basic"></a><span data-ttu-id="9882d-102">Shared (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9882d-102">Shared (Visual Basic)</span></span>
<span data-ttu-id="9882d-103">Určuje, že nejmíň jeden deklarovaný programový prvek je přidružená k třídě nebo struktuře ve velkém a ne s konkrétní instanci dané třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="9882d-103">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9882d-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9882d-104">Remarks</span></span>  
  
## <a name="when-to-use-shared"></a><span data-ttu-id="9882d-105">Kdy použít sdílené</span><span class="sxs-lookup"><span data-stu-id="9882d-105">When to Use Shared</span></span>  
 <span data-ttu-id="9882d-106">Sdílení členem třídy nebo struktury je k dispozici pro každou instanci spíše než *nesdílené*, kde každá instance udržuje svůj vlastní kopie.</span><span class="sxs-lookup"><span data-stu-id="9882d-106">Sharing a member of a class or structure makes it available to every instance, rather than *nonshared*, where each instance keeps its own copy.</span></span> <span data-ttu-id="9882d-107">To je užitečné, například, pokud hodnota proměnné se vztahuje na celé aplikace.</span><span class="sxs-lookup"><span data-stu-id="9882d-107">This is useful, for example, if the value of a variable applies to the entire application.</span></span> <span data-ttu-id="9882d-108">Pokud deklarujete tuto proměnnou deklarovanou `Shared`, pak všechny instance přístup ke stejné umístění úložiště, a pokud jedna instance se změní hodnota proměnné, přístup všechny instance aktualizovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9882d-108">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span></span>  
  
 <span data-ttu-id="9882d-109">Sdílení nezmění úroveň přístupu členu.</span><span class="sxs-lookup"><span data-stu-id="9882d-109">Sharing does not alter the access level of a member.</span></span> <span data-ttu-id="9882d-110">Například je možné sdílet člena třídy a privátní (přístupný pouze uvnitř třídy), nebo nesdílené a public.</span><span class="sxs-lookup"><span data-stu-id="9882d-110">For example, a class member can be shared and private (accessible only from within the class), or nonshared and public.</span></span> <span data-ttu-id="9882d-111">Další informace najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="9882d-111">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="9882d-112">pravidla</span><span class="sxs-lookup"><span data-stu-id="9882d-112">Rules</span></span>  
  
-   <span data-ttu-id="9882d-113">**Místní deklarace.**</span><span class="sxs-lookup"><span data-stu-id="9882d-113">**Declaration Context.**</span></span> <span data-ttu-id="9882d-114">Můžete použít `Shared` pouze na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="9882d-114">You can use `Shared` only at module level.</span></span> <span data-ttu-id="9882d-115">To znamená, že deklarace kontext `Shared` elementu musí být třídou nebo strukturou a nemůže být zdrojový soubor, obor názvů nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="9882d-115">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span></span>  
  
-   <span data-ttu-id="9882d-116">**Kombinované modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="9882d-116">**Combined Modifiers.**</span></span> <span data-ttu-id="9882d-117">Nelze zadat `Shared` spolu s [přepíše](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), nebo [ Statické](../../../visual-basic/language-reference/modifiers/static.md) ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="9882d-117">You cannot specify `Shared` together with [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), or [Static](../../../visual-basic/language-reference/modifiers/static.md) in the same declaration.</span></span>  
  
-   <span data-ttu-id="9882d-118">**Přístup k.**</span><span class="sxs-lookup"><span data-stu-id="9882d-118">**Accessing.**</span></span> <span data-ttu-id="9882d-119">Přístup sdíleného element ho kvalifikaci pomocí názvu třídy nebo struktury, nikoli název proměnné o konkrétní instanci její třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="9882d-119">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span></span> <span data-ttu-id="9882d-120">Ještě nemáte k vytvoření instance třídy nebo struktury pro přístup k její sdílené členy.</span><span class="sxs-lookup"><span data-stu-id="9882d-120">You do not even have to create an instance of a class or structure to access its shared members.</span></span>  
  
     <span data-ttu-id="9882d-121">Následující příklad volá sdílený postup <xref:System.Double.IsNaN%2A> vystavené <xref:System.Double> struktury.</span><span class="sxs-lookup"><span data-stu-id="9882d-121">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span></span>  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   <span data-ttu-id="9882d-122">**Implicitní sdílení.**</span><span class="sxs-lookup"><span data-stu-id="9882d-122">**Implicit Sharing.**</span></span> <span data-ttu-id="9882d-123">Nelze použít `Shared` modifikátor v [Const příkaz](../../../visual-basic/language-reference/statements/const-statement.md), ale konstanty jsou implicitně sdílené.</span><span class="sxs-lookup"><span data-stu-id="9882d-123">You cannot use the `Shared` modifier in a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md), but constants are implicitly shared.</span></span> <span data-ttu-id="9882d-124">Podobně nelze deklarovat člen modul nebo rozhraní být `Shared`, ale jsou implicitně sdílené.</span><span class="sxs-lookup"><span data-stu-id="9882d-124">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="9882d-125">Chování</span><span class="sxs-lookup"><span data-stu-id="9882d-125">Behavior</span></span>  
  
-   <span data-ttu-id="9882d-126">**Úložiště.**</span><span class="sxs-lookup"><span data-stu-id="9882d-126">**Storage.**</span></span> <span data-ttu-id="9882d-127">Sdílené proměnné nebo událostí je uložen v paměti pouze jednou, bez ohledu na to, kolik nebo několik instancí vytvořit jeho třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="9882d-127">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span></span> <span data-ttu-id="9882d-128">Podobně sdílený postup nebo vlastnost obsahuje pouze jednu sadu lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="9882d-128">Similarly, a shared procedure or property holds only one set of local variables.</span></span>  
  
-   <span data-ttu-id="9882d-129">**Přístup k prostřednictvím proměnné Instance.**</span><span class="sxs-lookup"><span data-stu-id="9882d-129">**Accessing through an Instance Variable.**</span></span> <span data-ttu-id="9882d-130">Je možné pro přístup k prvku sdílené kvalifikaci s názvem proměnné, která obsahuje konkrétní instanci její třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="9882d-130">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span></span> <span data-ttu-id="9882d-131">I když to obvykle funguje podle očekávání, kompilátor vygeneruje upozornění a zajišťuje tak přístup prostřednictvím názvu třídy nebo struktury namísto proměnné.</span><span class="sxs-lookup"><span data-stu-id="9882d-131">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span></span>  
  
-   <span data-ttu-id="9882d-132">**Přístup prostřednictvím výrazu Instance.**</span><span class="sxs-lookup"><span data-stu-id="9882d-132">**Accessing through an Instance Expression.**</span></span> <span data-ttu-id="9882d-133">Pokud element sdílené přistupujete prostřednictvím výraz, který vrací instanci její třídy nebo struktury, kompilátor provede přístup pomocí názvu třídy nebo struktury místo vyhodnocení výrazu.</span><span class="sxs-lookup"><span data-stu-id="9882d-133">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span></span> <span data-ttu-id="9882d-134">Pokud jste zamýšleli výraz, který má provádět další akce, jakož i vrací instanci výsledkem neočekávané výsledky.</span><span class="sxs-lookup"><span data-stu-id="9882d-134">This produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span></span> <span data-ttu-id="9882d-135">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="9882d-135">The following example illustrates this.</span></span>  
  
    ```vb
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
  
     <span data-ttu-id="9882d-136">V předchozím příkladu, kompilátor vygeneruje upozornění obou časů kód přistupuje ke sdílené proměnné `total` prostřednictvím instance.</span><span class="sxs-lookup"><span data-stu-id="9882d-136">In the preceding example, the compiler generates a warning message both times the code accesses the shared variable `total` through an instance.</span></span> <span data-ttu-id="9882d-137">V každém případě je přístup přímo prostřednictvím třídy `shareTotal` a neprovede použít jakékoli instance.</span><span class="sxs-lookup"><span data-stu-id="9882d-137">In each case it makes the access directly through the class `shareTotal` and does not make use of any instance.</span></span> <span data-ttu-id="9882d-138">V případě zamýšlený volání do procedury `returnClass`, to znamená, že i negeneruje volání `returnClass`, takže není provádět další akce zobrazení "Volá funkci returnClass()".</span><span class="sxs-lookup"><span data-stu-id="9882d-138">In the case of the intended call to the procedure `returnClass`, this means it does not even generate a call to `returnClass`, so the additional action of displaying "Function returnClass() called" is not performed.</span></span>  
  
 <span data-ttu-id="9882d-139">`Shared` Modifikátor lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="9882d-139">The `Shared` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="9882d-140">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="9882d-140">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="9882d-141">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="9882d-141">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="9882d-142">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="9882d-142">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="9882d-143">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="9882d-143">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="9882d-144">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="9882d-144">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="9882d-145">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="9882d-145">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="9882d-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="9882d-146">See Also</span></span>  
 [<span data-ttu-id="9882d-147">Shadows</span><span class="sxs-lookup"><span data-stu-id="9882d-147">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="9882d-148">Static</span><span class="sxs-lookup"><span data-stu-id="9882d-148">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)  
 [<span data-ttu-id="9882d-149">Doba platnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9882d-149">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="9882d-150">Procedury</span><span class="sxs-lookup"><span data-stu-id="9882d-150">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="9882d-151">Struktury</span><span class="sxs-lookup"><span data-stu-id="9882d-151">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="9882d-152">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="9882d-152">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
