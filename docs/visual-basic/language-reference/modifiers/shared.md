---
title: Shared
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
ms.openlocfilehash: bc63de4bda1e8e605e25fbe293686c187dd4d005
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290990"
---
# <a name="shared-visual-basic"></a><span data-ttu-id="6cf68-102">Shared (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6cf68-102">Shared (Visual Basic)</span></span>

<span data-ttu-id="6cf68-103">Určuje, že nejmíň jeden deklarovaný programový prvek je spojen s třídou nebo strukturou ve velkém, a nikoli s konkrétní instancí třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="6cf68-103">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span></span>

## <a name="when-to-use-shared"></a><span data-ttu-id="6cf68-104">Kdy použít Shared</span><span class="sxs-lookup"><span data-stu-id="6cf68-104">When to Use Shared</span></span>

<span data-ttu-id="6cf68-105">Sdílení člena třídy nebo struktury zpřístupňuje každou instanci, nikoli *nesdílenou*, kde každá instance udržuje svou vlastní kopii.</span><span class="sxs-lookup"><span data-stu-id="6cf68-105">Sharing a member of a class or structure makes it available to every instance, rather than *non-shared*, where each instance keeps its own copy.</span></span> <span data-ttu-id="6cf68-106">To je užitečné, například pokud se hodnota proměnné vztahuje na celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6cf68-106">This is useful, for example, if the value of a variable applies to the entire application.</span></span> <span data-ttu-id="6cf68-107">Pokud deklarujete tuto proměnnou `Shared` , pak všechny instance budou přistupovat ke stejnému umístění úložiště a pokud jedna instance změní hodnotu proměnné, všechny instance budou přistupovat k aktualizované hodnotě.</span><span class="sxs-lookup"><span data-stu-id="6cf68-107">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span></span>

<span data-ttu-id="6cf68-108">Sdílení nemění úroveň přístupu člena.</span><span class="sxs-lookup"><span data-stu-id="6cf68-108">Sharing does not alter the access level of a member.</span></span> <span data-ttu-id="6cf68-109">Například člen třídy může být sdílen a soukromý (přístupný pouze z třídy) nebo nesdílené a veřejné.</span><span class="sxs-lookup"><span data-stu-id="6cf68-109">For example, a class member can be shared and private (accessible only from within the class), or non-shared and public.</span></span> <span data-ttu-id="6cf68-110">Další informace najdete v tématu [úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="6cf68-110">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

## <a name="rules"></a><span data-ttu-id="6cf68-111">Pravidla</span><span class="sxs-lookup"><span data-stu-id="6cf68-111">Rules</span></span>

- <span data-ttu-id="6cf68-112">**Kontext deklarace**</span><span class="sxs-lookup"><span data-stu-id="6cf68-112">**Declaration Context.**</span></span> <span data-ttu-id="6cf68-113">Můžete použít `Shared` pouze na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="6cf68-113">You can use `Shared` only at module level.</span></span> <span data-ttu-id="6cf68-114">To znamená, že kontext deklarace pro `Shared` prvek musí být třída nebo struktura a nemůže se jednat o zdrojový soubor, obor názvů nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="6cf68-114">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span></span>

- <span data-ttu-id="6cf68-115">**Kombinované modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="6cf68-115">**Combined Modifiers.**</span></span> <span data-ttu-id="6cf68-116">`Shared`V rámci stejné deklarace nelze zadat společně s [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)nebo [static](../../../visual-basic/language-reference/modifiers/static.md) .</span><span class="sxs-lookup"><span data-stu-id="6cf68-116">You cannot specify `Shared` together with [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), or [Static](../../../visual-basic/language-reference/modifiers/static.md) in the same declaration.</span></span>

- <span data-ttu-id="6cf68-117">**Přístup k.**</span><span class="sxs-lookup"><span data-stu-id="6cf68-117">**Accessing.**</span></span> <span data-ttu-id="6cf68-118">Ke sdílenému elementu přistupujete tak, že ho zařadíte s názvem jeho třídy nebo struktury, nikoli s názvem proměnné konkrétní instance své třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="6cf68-118">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span></span> <span data-ttu-id="6cf68-119">Pro přístup ke sdíleným členům nemusíte ani vytvářet instanci třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="6cf68-119">You do not even have to create an instance of a class or structure to access its shared members.</span></span>

     <span data-ttu-id="6cf68-120">V následujícím příkladu je volána sdílená procedura <xref:System.Double.IsNaN%2A> vystavená <xref:System.Double> strukturou.</span><span class="sxs-lookup"><span data-stu-id="6cf68-120">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span></span>

     ```vb
     If Double.IsNaN(result) Then Console.WriteLine("Result is mathematically undefined.")
     ```

- <span data-ttu-id="6cf68-121">**Implicitní sdílení.**</span><span class="sxs-lookup"><span data-stu-id="6cf68-121">**Implicit Sharing.**</span></span> <span data-ttu-id="6cf68-122">`Shared`V [příkazu const](../../../visual-basic/language-reference/statements/const-statement.md)nelze použít modifikátor, ale konstanty jsou implicitně sdíleny.</span><span class="sxs-lookup"><span data-stu-id="6cf68-122">You cannot use the `Shared` modifier in a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md), but constants are implicitly shared.</span></span> <span data-ttu-id="6cf68-123">Podobně nemůžete deklarovat člen modulu nebo rozhraní, které mají být `Shared` , ale budou implicitně sdíleny.</span><span class="sxs-lookup"><span data-stu-id="6cf68-123">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span></span>

## <a name="behavior"></a><span data-ttu-id="6cf68-124">Chování</span><span class="sxs-lookup"><span data-stu-id="6cf68-124">Behavior</span></span>

- <span data-ttu-id="6cf68-125">**Pamì.**</span><span class="sxs-lookup"><span data-stu-id="6cf68-125">**Storage.**</span></span> <span data-ttu-id="6cf68-126">Sdílená proměnná nebo událost je uložena v paměti pouze jednou, bez ohledu na to, kolik instancí tvoří svou třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="6cf68-126">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span></span> <span data-ttu-id="6cf68-127">Podobně sdílená procedura nebo vlastnost obsahuje pouze jednu sadu místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="6cf68-127">Similarly, a shared procedure or property holds only one set of local variables.</span></span>

- <span data-ttu-id="6cf68-128">**Přístup prostřednictvím proměnné instance.**</span><span class="sxs-lookup"><span data-stu-id="6cf68-128">**Accessing through an Instance Variable.**</span></span> <span data-ttu-id="6cf68-129">Je možné přistupovat ke sdílenému prvku tím, že je kvalifikován s názvem proměnné, která obsahuje konkrétní instanci své třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="6cf68-129">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span></span> <span data-ttu-id="6cf68-130">I když to obvykle funguje podle očekávání, kompilátor vygeneruje zprávu upozornění a provede přístup prostřednictvím třídy nebo názvu struktury namísto proměnné.</span><span class="sxs-lookup"><span data-stu-id="6cf68-130">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span></span>

- <span data-ttu-id="6cf68-131">**Přístup prostřednictvím výrazu instance.**</span><span class="sxs-lookup"><span data-stu-id="6cf68-131">**Accessing through an Instance Expression.**</span></span> <span data-ttu-id="6cf68-132">Pokud přistupujete ke sdílenému prvku prostřednictvím výrazu, který vrací instanci své třídy nebo struktury, kompilátor provede přístup prostřednictvím třídy nebo názvu struktury namísto vyhodnocení výrazu.</span><span class="sxs-lookup"><span data-stu-id="6cf68-132">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span></span> <span data-ttu-id="6cf68-133">Výsledkem je neočekávané výsledky, pokud jste určili výraz k provádění dalších akcí a také k vrácení instance.</span><span class="sxs-lookup"><span data-stu-id="6cf68-133">This produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span></span> <span data-ttu-id="6cf68-134">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="6cf68-134">The following example illustrates this.</span></span>
  
    ```vb
    Sub Main()
        ' The following line is the preferred way to access Total.
        ShareTotal.Total = 10

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of through
        ' the variable instanceVar. This works as expected and adds
        ' 100 to Total.
        Dim instanceVar As New ShareTotal
        instanceVar.Total += 100

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of calling
        ' ReturnClass(). This adds 1000 to total but does not work as
        ' expected, because the WriteLine in ReturnClass() does not run.
        Console.WriteLine("Value of total is " & CStr(ShareTotal.Total))
        ReturnClass().Total += 1000
    End Sub

    Public Function ReturnClass() As ShareTotal
        Console.WriteLine("Function ReturnClass() called")
        Return New ShareTotal
    End Function

    Public Class ShareTotal
        Public Shared Property Total As Integer
    End Class
    ```

     <span data-ttu-id="6cf68-135">V předchozím příkladu kompilátor vygeneruje zprávu upozornění pokaždé, když kód přistupuje ke sdílené vlastnosti `Total` prostřednictvím instance.</span><span class="sxs-lookup"><span data-stu-id="6cf68-135">In the preceding example, the compiler generates a warning message both times the code accesses the shared property `Total` through an instance.</span></span> <span data-ttu-id="6cf68-136">V každém případě přistupuje přímo přes třídu `ShareTotal` a nevyužívá žádné instance.</span><span class="sxs-lookup"><span data-stu-id="6cf68-136">In each case it makes the access directly through the class `ShareTotal` and does not make use of any instance.</span></span> <span data-ttu-id="6cf68-137">V případě zamýšleného volání procedury `ReturnClass` to znamená, že ani negeneruje volání `ReturnClass` , takže se neprovádí další akce zobrazení "Function ReturnClass () s názvem".</span><span class="sxs-lookup"><span data-stu-id="6cf68-137">In the case of the intended call to the procedure `ReturnClass`, this means it does not even generate a call to `ReturnClass`, so the additional action of displaying "Function ReturnClass() called" is not performed.</span></span>

<span data-ttu-id="6cf68-138">`Shared`V těchto kontextech lze použít modifikátor:</span><span class="sxs-lookup"><span data-stu-id="6cf68-138">The `Shared` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="6cf68-139">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="6cf68-139">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="6cf68-140">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="6cf68-140">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="6cf68-141">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="6cf68-141">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="6cf68-142">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="6cf68-142">Operator Statement</span></span>](../operator-statement.md)
- [<span data-ttu-id="6cf68-143">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="6cf68-143">Property Statement</span></span>](../property-statement.md)
- [<span data-ttu-id="6cf68-144">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="6cf68-144">Sub Statement</span></span>](../sub-statement.md)
  
## <a name="see-also"></a><span data-ttu-id="6cf68-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="6cf68-145">See also</span></span>

- [<span data-ttu-id="6cf68-146">Shadows</span><span class="sxs-lookup"><span data-stu-id="6cf68-146">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="6cf68-147">Tras</span><span class="sxs-lookup"><span data-stu-id="6cf68-147">Static</span></span>](static.md)
- [<span data-ttu-id="6cf68-148">Doba platnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6cf68-148">Lifetime in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="6cf68-149">Procedury</span><span class="sxs-lookup"><span data-stu-id="6cf68-149">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="6cf68-150">Struktury</span><span class="sxs-lookup"><span data-stu-id="6cf68-150">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="6cf68-151">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="6cf68-151">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
