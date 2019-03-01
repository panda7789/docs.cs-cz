---
title: Automaticky implementované vlastnosti (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: 56ea9bac1326ebab7ef44fb5541c05be8bc855e7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967201"
---
# <a name="auto-implemented-properties-visual-basic"></a><span data-ttu-id="9fe18-102">Automaticky implementované vlastnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fe18-102">Auto-Implemented Properties (Visual Basic)</span></span>
<span data-ttu-id="9fe18-103">*Automaticky implementované vlastnosti* vám umožní rychle určit vlastnost třídy, aniž byste museli napsat kód, který `Get` a `Set` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9fe18-103">*Auto-implemented properties* enable you to quickly specify a property of a class without having to write code to `Get` and `Set` the property.</span></span> <span data-ttu-id="9fe18-104">Při psaní kódu pro automaticky implementovanou vlastnost kompilátor jazyka Visual Basic automaticky vytvoří soukromé pole k uložení proměnné vlastnost kromě vytvoření přidružený `Get` a `Set` postupy.</span><span class="sxs-lookup"><span data-stu-id="9fe18-104">When you write code for an auto-implemented property, the Visual Basic compiler automatically creates a private field to store the property variable in addition to creating the associated `Get` and `Set` procedures.</span></span>  
  
 <span data-ttu-id="9fe18-105">S automaticky implementovanými vlastnostmi lze deklarovat vlastnosti, včetně výchozí hodnotu, na jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="9fe18-105">With auto-implemented properties, a property, including a default value, can be declared in a single line.</span></span> <span data-ttu-id="9fe18-106">Následující příklad ukazuje tři vlastnosti deklarací.</span><span class="sxs-lookup"><span data-stu-id="9fe18-106">The following example shows three property declarations.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#1)]  
  
 <span data-ttu-id="9fe18-107">Automaticky implementované vlastnosti je ekvivalentní k vlastnosti, kterou je uložená hodnota vlastnosti v soukromé pole.</span><span class="sxs-lookup"><span data-stu-id="9fe18-107">An auto-implemented property is equivalent to a property for which the property value is stored in a private field.</span></span> <span data-ttu-id="9fe18-108">Následující příklad kódu ukazuje automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9fe18-108">The following code example shows an auto-implemented property.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#5)]  
  
 <span data-ttu-id="9fe18-109">Následující příklad kódu ukazuje odpovídající kód z předchozího příkladu automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9fe18-109">The following code example shows the equivalent code for the previous auto-implemented property example.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#2)]  
  
 <span data-ttu-id="9fe18-110">Následující kód zobrazí implementace vlastnosti jen pro čtení:</span><span class="sxs-lookup"><span data-stu-id="9fe18-110">The following code show implementing readonly properties:</span></span>  
  
```vb  
Class Customer  
   Public ReadOnly Property Tags As New List(Of String)  
   Public ReadOnly Property Name As String = ""  
   Public ReadOnly Property File As String  
  
   Sub New(file As String)  
      Me.File = file  
   End Sub  
End Class  
```  
  
 <span data-ttu-id="9fe18-111">Můžete přiřadit k vlastnosti s výrazy inicializace, jak je znázorněno v příkladu, nebo můžete přiřadit k vlastnosti v konstruktoru nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="9fe18-111">You can assign to the property with initialization expressions as shown in the example, or you can assign to the properties in the containing type’s constructor.</span></span>  <span data-ttu-id="9fe18-112">Kdykoli můžete přiřadit do pole základní vlastnosti jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="9fe18-112">You can assign to the backing fields of readonly properties at any time.</span></span>  
  
## <a name="backing-field"></a><span data-ttu-id="9fe18-113">Zálohovací položka</span><span class="sxs-lookup"><span data-stu-id="9fe18-113">Backing Field</span></span>  
 <span data-ttu-id="9fe18-114">Při deklaraci automaticky implementovaná vlastnost jazyka Visual Basic automaticky vytvoří skrytou privátní pole s názvem *pomocné pole* tak, aby obsahovala hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9fe18-114">When you declare an auto-implemented property, Visual Basic automatically creates a hidden private field called the *backing field* to contain the property value.</span></span> <span data-ttu-id="9fe18-115">Název pomocné pole je název automaticky implementované vlastnosti začínající podtržítkem (_).</span><span class="sxs-lookup"><span data-stu-id="9fe18-115">The backing field name is the auto-implemented property name preceded by an underscore (_).</span></span> <span data-ttu-id="9fe18-116">Například, pokud deklarujete automaticky implementovaná vlastnost s názvem `ID`, se s pomocným polem názvem `_ID`.</span><span class="sxs-lookup"><span data-stu-id="9fe18-116">For example, if you declare an auto-implemented property named `ID`, the backing field is named `_ID`.</span></span> <span data-ttu-id="9fe18-117">Pokud zahrnete člena vaší třídy, která se také nazývá `_ID`, vytvářejí konfliktu názvů a Visual Basic hlásí chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="9fe18-117">If you include a member of your class that is also named `_ID`, you produce a naming conflict and Visual Basic reports a compiler error.</span></span>  
  
 <span data-ttu-id="9fe18-118">Pomocné pole také má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="9fe18-118">The backing field also has the following characteristics:</span></span>  
  
-   <span data-ttu-id="9fe18-119">Modifikátor přístupu pro pomocné pole je vždy `Private`, i když samotné vlastnosti má úroveň různý přístup, jako například `Public`.</span><span class="sxs-lookup"><span data-stu-id="9fe18-119">The access modifier for the backing field is always `Private`, even when the property itself has a different access level, such as `Public`.</span></span>  
  
-   <span data-ttu-id="9fe18-120">Pokud je vlastnost označená jako `Shared`, také sdílet pomocným polem.</span><span class="sxs-lookup"><span data-stu-id="9fe18-120">If the property is marked as `Shared`, the backing field also is shared.</span></span>  
  
-   <span data-ttu-id="9fe18-121">Atributy určené pro vlastnost se nevztahují na pomocné pole.</span><span class="sxs-lookup"><span data-stu-id="9fe18-121">Attributes specified for the property do not apply to the backing field.</span></span>  
  
-   <span data-ttu-id="9fe18-122">Pomocné pole jsou přístupné z kódu v rámci třídy a ladicí nástroje, jako jsou okna kukátka.</span><span class="sxs-lookup"><span data-stu-id="9fe18-122">The backing field can be accessed from code within the class and from debugging tools such as the Watch window.</span></span> <span data-ttu-id="9fe18-123">Pomocné pole není uveden v seznamu pro doplňování slov technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="9fe18-123">However, the backing field does not show in an IntelliSense word completion list.</span></span>  
  
## <a name="initializing-an-auto-implemented-property"></a><span data-ttu-id="9fe18-124">Inicializuje se automaticky implementované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9fe18-124">Initializing an Auto-Implemented Property</span></span>  
 <span data-ttu-id="9fe18-125">Libovolný výraz, který slouží k inicializaci pole je platný pro inicializaci automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9fe18-125">Any expression that can be used to initialize a field is valid for initializing an auto-implemented property.</span></span> <span data-ttu-id="9fe18-126">Při inicializaci automaticky implementované vlastnosti výraz je vyhodnocen a předat `Set` postup pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9fe18-126">When you initialize an auto-implemented property, the expression is evaluated and passed to the `Set` procedure for the property.</span></span> <span data-ttu-id="9fe18-127">Následující příklady kódu ukazují některé automaticky implementované vlastnosti, které obsahují počáteční hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9fe18-127">The following code examples show some auto-implemented properties that include initial values.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 <span data-ttu-id="9fe18-128">Nelze inicializovat automaticky implementované vlastnosti, který je členem `Interface`, nebo disk, který je označen `MustOverride`.</span><span class="sxs-lookup"><span data-stu-id="9fe18-128">You cannot initialize an auto-implemented property that is a member of an `Interface`, or one that is marked `MustOverride`.</span></span>  
  
 <span data-ttu-id="9fe18-129">Pokud deklarujete automaticky implementované vlastnosti jako člen `Structure`, automaticky implementované vlastnosti lze inicializovat pouze pokud je označen jako `Shared`.</span><span class="sxs-lookup"><span data-stu-id="9fe18-129">When you declare an auto-implemented property as a member of a `Structure`, you can only initialize the auto-implemented property if it is marked as `Shared`.</span></span>  
  
 <span data-ttu-id="9fe18-130">Když deklarujete automaticky implementované vlastnosti jako pole, nelze zadat explicitní pole hranice.</span><span class="sxs-lookup"><span data-stu-id="9fe18-130">When you declare an auto-implemented property as an array, you cannot specify explicit array bounds.</span></span> <span data-ttu-id="9fe18-131">Můžete však zadat hodnotu pomocí inicializátoru pole, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9fe18-131">However, you can supply a value by using an array initializer, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a><span data-ttu-id="9fe18-132">Definice vlastností, které vyžadují standardní syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fe18-132">Property Definitions That Require Standard Syntax</span></span>  
 <span data-ttu-id="9fe18-133">Automaticky implementované vlastnosti jsou pohodlný a podporují řadu programovacích scénářů.</span><span class="sxs-lookup"><span data-stu-id="9fe18-133">Auto-implemented properties are convenient and support many programming scenarios.</span></span> <span data-ttu-id="9fe18-134">Existují však situace, kdy nejde používat automaticky implementované vlastnosti a musíte místo toho použít standardní, nebo *rozšířit*, syntaxe vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9fe18-134">However, there are situations in which you cannot use an auto-implemented property and must instead use standard, or *expanded*, property syntax.</span></span>  
  
 <span data-ttu-id="9fe18-135">Budete muset použít syntaxe rozšířené definici vlastnosti, pokud chcete provádět žádnou z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="9fe18-135">You have to use expanded property-definition syntax if you want to do any one of the following:</span></span>  
  
-   <span data-ttu-id="9fe18-136">Přidejte kód, který `Get` nebo `Set` procedury vlastnosti, jako je například kód pro ověření příchozích hodnot v `Set` postup.</span><span class="sxs-lookup"><span data-stu-id="9fe18-136">Add code to the `Get` or `Set` procedure of a property, such as code to validate incoming values in the `Set` procedure.</span></span> <span data-ttu-id="9fe18-137">Například můžete chtít ověřit, jestli řetězec, který představuje telefonní číslo obsahuje požadovaný počet číslic než nastavení hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9fe18-137">For example, you might want to verify that a string that represents a telephone number contains the required number of numerals before setting the property value.</span></span>  
  
-   <span data-ttu-id="9fe18-138">Zadejte jiný usnadnění pro `Get` a `Set` postup.</span><span class="sxs-lookup"><span data-stu-id="9fe18-138">Specify different accessibility for the `Get` and `Set` procedure.</span></span> <span data-ttu-id="9fe18-139">Například můžete chtít provést `Set` postup `Private` a `Get` postup `Public`.</span><span class="sxs-lookup"><span data-stu-id="9fe18-139">For example, you might want to make the `Set` procedure `Private` and the `Get` procedure `Public`.</span></span>  
  
-   <span data-ttu-id="9fe18-140">Vytvoření vlastnosti, které jsou `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="9fe18-140">Create properties that are `WriteOnly`.</span></span>  
  
-   <span data-ttu-id="9fe18-141">Použití parametrizovaného vlastností (včetně `Default` vlastnosti).</span><span class="sxs-lookup"><span data-stu-id="9fe18-141">Use parameterized properties (including `Default` properties).</span></span> <span data-ttu-id="9fe18-142">Rozšířené vlastnosti musí deklarovat, pokud chcete zadat parametr pro vlastnost, nebo k zadání dalších parametrů pro `Set` postup.</span><span class="sxs-lookup"><span data-stu-id="9fe18-142">You must declare an expanded property in order to specify a parameter for the property, or to specify additional parameters for the `Set` procedure.</span></span>  
  
-   <span data-ttu-id="9fe18-143">Umístit atribut na pomocné pole nebo změnit úroveň přístupu pomocným polem.</span><span class="sxs-lookup"><span data-stu-id="9fe18-143">Place an attribute on the backing field, or change the access level of the backing field.</span></span>  
  
-   <span data-ttu-id="9fe18-144">Komentáře XML zadejte pro pole zálohování.</span><span class="sxs-lookup"><span data-stu-id="9fe18-144">Provide XML comments for the backing field.</span></span>  
  
## <a name="expanding-an-auto-implemented-property"></a><span data-ttu-id="9fe18-145">Automaticky implementované vlastnosti rozšíření</span><span class="sxs-lookup"><span data-stu-id="9fe18-145">Expanding an Auto-Implemented Property</span></span>  
 <span data-ttu-id="9fe18-146">Pokud budete muset převést na rozšířenou vlastnost, která obsahuje automaticky implementované vlastnosti `Get` nebo `Set` postupu, Editor kódu jazyka Visual Basic můžete automaticky vygenerovat `Get` a `Set` postupy a `End Property`příkaz Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9fe18-146">If you have to convert an auto-implemented property to an expanded property that contains a `Get` or `Set` procedure, the Visual Basic Code Editor can automatically generate the `Get` and `Set` procedures and `End Property` statement for the property.</span></span> <span data-ttu-id="9fe18-147">Kód je generována, pokud umístěte kurzor na prázdný řádek následující `Property` příkazu, zadejte `G` (pro `Get`) nebo `S` (pro `Set`) a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="9fe18-147">The code is generated if you put the cursor on a blank line following the `Property` statement, type a `G` (for `Get`) or an `S` (for `Set`) and press ENTER.</span></span> <span data-ttu-id="9fe18-148">Editor kódu jazyka Visual Basic generuje automaticky `Get` nebo `Set` postup pro vlastnosti jen pro čtení a jen pro zápis při stisknutí klávesy ENTER na konci `Property` příkazu.</span><span class="sxs-lookup"><span data-stu-id="9fe18-148">The Visual Basic Code Editor automatically generates the `Get` or `Set` procedure for read-only and write-only properties when you press ENTER at the end of a `Property` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fe18-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9fe18-149">See also</span></span>
- [<span data-ttu-id="9fe18-150">Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9fe18-150">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="9fe18-151">Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="9fe18-151">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="9fe18-152">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="9fe18-152">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="9fe18-153">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="9fe18-153">ReadOnly</span></span>](../../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="9fe18-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="9fe18-154">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="9fe18-155">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="9fe18-155">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
