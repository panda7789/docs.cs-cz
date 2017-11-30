---
title: "Automaticky implementované vlastnosti (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 507d91f6176eb8bc3888be6f9843b5ffdd28a08f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="auto-implemented-properties-visual-basic"></a><span data-ttu-id="cc425-102">Automaticky implementované vlastnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc425-102">Auto-Implemented Properties (Visual Basic)</span></span>
<span data-ttu-id="cc425-103">*Automaticky implementované vlastnosti* vám umožní rychle určit vlastnost třídy bez nutnosti psaní kódu pro `Get` a `Set` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cc425-103">*Auto-implemented properties* enable you to quickly specify a property of a class without having to write code to `Get` and `Set` the property.</span></span> <span data-ttu-id="cc425-104">Při psaní kódu automaticky implementované vlastnosti, Visual Basic – kompilátor automaticky vytvoří privátní pole pro uložení proměnné vlastnost kromě vytváření přidruženého `Get` a `Set` postupy.</span><span class="sxs-lookup"><span data-stu-id="cc425-104">When you write code for an auto-implemented property, the Visual Basic compiler automatically creates a private field to store the property variable in addition to creating the associated `Get` and `Set` procedures.</span></span>  
  
 <span data-ttu-id="cc425-105">S automaticky implementované vlastnosti vlastnosti, včetně výchozí hodnotu, lze deklarovat na jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="cc425-105">With auto-implemented properties, a property, including a default value, can be declared in a single line.</span></span> <span data-ttu-id="cc425-106">Následující příklad ukazuje tři vlastnosti deklarací.</span><span class="sxs-lookup"><span data-stu-id="cc425-106">The following example shows three property declarations.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](./codesnippet/VisualBasic/auto-implemented-properties_1.vb)]  
  
 <span data-ttu-id="cc425-107">Ve automaticky implementované vlastnosti je stejná jako vlastnost, pro kterou je hodnota vlastnosti uložené v soukromé pole.</span><span class="sxs-lookup"><span data-stu-id="cc425-107">An auto-implemented property is equivalent to a property for which the property value is stored in a private field.</span></span> <span data-ttu-id="cc425-108">Následující příklad kódu ukazuje ve automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cc425-108">The following code example shows an auto-implemented property.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](./codesnippet/VisualBasic/auto-implemented-properties_2.vb)]  
  
 <span data-ttu-id="cc425-109">Následující příklad kódu ukazuje kód ekvivalentní pro předchozí příklad automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cc425-109">The following code example shows the equivalent code for the previous auto-implemented property example.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](./codesnippet/VisualBasic/auto-implemented-properties_3.vb)]  
  
 <span data-ttu-id="cc425-110">Následující kód zobrazit implementace vlastnosti jen pro čtení:</span><span class="sxs-lookup"><span data-stu-id="cc425-110">The following code show implementing readonly properties:</span></span>  
  
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
  
 <span data-ttu-id="cc425-111">Můžete přiřadit k vlastnosti s inicializace výrazy, jak je znázorněno v příkladu, nebo můžete přiřadit k vlastnosti v konstruktoru obsahující typu.</span><span class="sxs-lookup"><span data-stu-id="cc425-111">You can assign to the property with initialization expressions as shown in the example, or you can assign to the properties in the containing type’s constructor.</span></span>  <span data-ttu-id="cc425-112">Kdykoli můžete přiřadit na pole základní vlastnosti jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="cc425-112">You can assign to the backing fields of readonly properties at any time.</span></span>  
  
## <a name="backing-field"></a><span data-ttu-id="cc425-113">Základní pole</span><span class="sxs-lookup"><span data-stu-id="cc425-113">Backing Field</span></span>  
 <span data-ttu-id="cc425-114">Když je deklarovat ve automaticky implementované vlastnosti, Visual Basic automaticky vytvoří privátní skrytá pole s názvem *základní pole* tak, aby obsahovala hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cc425-114">When you declare an auto-implemented property, Visual Basic automatically creates a hidden private field called the *backing field* to contain the property value.</span></span> <span data-ttu-id="cc425-115">Název pole nástroje zálohování je název automaticky implementované vlastnosti sebou podtržítko (_).</span><span class="sxs-lookup"><span data-stu-id="cc425-115">The backing field name is the auto-implemented property name preceded by an underscore (_).</span></span> <span data-ttu-id="cc425-116">Například, pokud je deklarovat ve automaticky implementované vlastnosti s názvem `ID`, má název pole Základní `_ID`.</span><span class="sxs-lookup"><span data-stu-id="cc425-116">For example, if you declare an auto-implemented property named `ID`, the backing field is named `_ID`.</span></span> <span data-ttu-id="cc425-117">Pokud zahrnete člena třídy, který je také název `_ID`, můžete vytvořit ke konfliktu názvů a hlásí chyby kompilátoru jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cc425-117">If you include a member of your class that is also named `_ID`, you produce a naming conflict and Visual Basic reports a compiler error.</span></span>  
  
 <span data-ttu-id="cc425-118">Pole Základní také má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="cc425-118">The backing field also has the following characteristics:</span></span>  
  
-   <span data-ttu-id="cc425-119">Modifikátor přístupu pro pole zálohování je vždy `Private`, i když samotné vlastnosti má úroveň různý přístup, jako například `Public`.</span><span class="sxs-lookup"><span data-stu-id="cc425-119">The access modifier for the backing field is always `Private`, even when the property itself has a different access level, such as `Public`.</span></span>  
  
-   <span data-ttu-id="cc425-120">Pokud je vlastnost označena jako `Shared`, také sdílet pole zálohování.</span><span class="sxs-lookup"><span data-stu-id="cc425-120">If the property is marked as `Shared`, the backing field also is shared.</span></span>  
  
-   <span data-ttu-id="cc425-121">Zadané atributy pro vlastnost se nevztahují na základní pole.</span><span class="sxs-lookup"><span data-stu-id="cc425-121">Attributes specified for the property do not apply to the backing field.</span></span>  
  
-   <span data-ttu-id="cc425-122">Základní pole jsou přístupné z kódu v rámci třídy a ladění nástrojů, jako je okno kukátka.</span><span class="sxs-lookup"><span data-stu-id="cc425-122">The backing field can be accessed from code within the class and from debugging tools such as the Watch window.</span></span> <span data-ttu-id="cc425-123">Pole Základní se však nezobrazuje v seznamu dokončení IntelliSense aplikace word.</span><span class="sxs-lookup"><span data-stu-id="cc425-123">However, the backing field does not show in an IntelliSense word completion list.</span></span>  
  
## <a name="initializing-an-auto-implemented-property"></a><span data-ttu-id="cc425-124">Inicializace ve automaticky implementované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="cc425-124">Initializing an Auto-Implemented Property</span></span>  
 <span data-ttu-id="cc425-125">Jakýkoli výraz, který slouží k inicializaci pole je platný pro inicializaci ve automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cc425-125">Any expression that can be used to initialize a field is valid for initializing an auto-implemented property.</span></span> <span data-ttu-id="cc425-126">Při inicializaci ve automaticky implementované vlastnosti je výraz vyhodnocen a předán `Set` postup pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cc425-126">When you initialize an auto-implemented property, the expression is evaluated and passed to the `Set` procedure for the property.</span></span> <span data-ttu-id="cc425-127">Následující příklady kódu ukazují některé automaticky implementované vlastnosti, které zahrnují počáteční hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cc425-127">The following code examples show some auto-implemented properties that include initial values.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](./codesnippet/VisualBasic/auto-implemented-properties_4.vb)]  
  
 <span data-ttu-id="cc425-128">Nelze inicializovat ve automaticky implementované vlastnosti, který je členem skupiny `Interface`, nebo takové, která je označena `MustOverride`.</span><span class="sxs-lookup"><span data-stu-id="cc425-128">You cannot initialize an auto-implemented property that is a member of an `Interface`, or one that is marked `MustOverride`.</span></span>  
  
 <span data-ttu-id="cc425-129">Když je deklarovat ve automaticky implementované vlastnosti jako člen skupiny `Structure`, automaticky implementované vlastnosti můžete inicializovat pouze pokud je označen jako `Shared`.</span><span class="sxs-lookup"><span data-stu-id="cc425-129">When you declare an auto-implemented property as a member of a `Structure`, you can only initialize the auto-implemented property if it is marked as `Shared`.</span></span>  
  
 <span data-ttu-id="cc425-130">Po deklarování ve automaticky implementované vlastnosti jako pole, nemůžete zadat explicitní pole hranice.</span><span class="sxs-lookup"><span data-stu-id="cc425-130">When you declare an auto-implemented property as an array, you cannot specify explicit array bounds.</span></span> <span data-ttu-id="cc425-131">Můžete však zadat hodnotu pomocí inicializátoru pole, podle následujících příkladů.</span><span class="sxs-lookup"><span data-stu-id="cc425-131">However, you can supply a value by using an array initializer, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](./codesnippet/VisualBasic/auto-implemented-properties_5.vb)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a><span data-ttu-id="cc425-132">Definice vlastností, které vyžadují standardní syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc425-132">Property Definitions That Require Standard Syntax</span></span>  
 <span data-ttu-id="cc425-133">Automaticky implementované vlastnosti jsou pohodlný a podporují mnoho scénáře programování.</span><span class="sxs-lookup"><span data-stu-id="cc425-133">Auto-implemented properties are convenient and support many programming scenarios.</span></span> <span data-ttu-id="cc425-134">Existují však situace, ve kterých nelze použít ve automaticky implementované vlastnosti a místo toho musíte použít standard, nebo *rozšířit*, vlastnost syntaxe.</span><span class="sxs-lookup"><span data-stu-id="cc425-134">However, there are situations in which you cannot use an auto-implemented property and must instead use standard, or *expanded*, property syntax.</span></span>  
  
 <span data-ttu-id="cc425-135">Budete muset použít rozšířené definici vlastnosti syntaxe, pokud budete chtít provést jednu z těchto možností:</span><span class="sxs-lookup"><span data-stu-id="cc425-135">You have to use expanded property-definition syntax if you want to do any one of the following:</span></span>  
  
-   <span data-ttu-id="cc425-136">Přidejte kód, který `Get` nebo `Set` postup vlastnosti, jako je například kódu k ověření příchozích hodnot v `Set` postupu.</span><span class="sxs-lookup"><span data-stu-id="cc425-136">Add code to the `Get` or `Set` procedure of a property, such as code to validate incoming values in the `Set` procedure.</span></span> <span data-ttu-id="cc425-137">Například můžete chtít ověřte, že řetězec, který představuje telefonní číslo obsahuje požadovaný počet číslic před nastavením hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cc425-137">For example, you might want to verify that a string that represents a telephone number contains the required number of numerals before setting the property value.</span></span>  
  
-   <span data-ttu-id="cc425-138">Zadejte jiný usnadnění pro `Get` a `Set` postupu.</span><span class="sxs-lookup"><span data-stu-id="cc425-138">Specify different accessibility for the `Get` and `Set` procedure.</span></span> <span data-ttu-id="cc425-139">Například můžete chtít provést `Set` postup `Private` a `Get` postup `Public`.</span><span class="sxs-lookup"><span data-stu-id="cc425-139">For example, you might want to make the `Set` procedure `Private` and the `Get` procedure `Public`.</span></span>  
  
-   <span data-ttu-id="cc425-140">Vytvoření vlastnosti, které jsou `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="cc425-140">Create properties that are `WriteOnly`.</span></span>  
  
-   <span data-ttu-id="cc425-141">Použití parametrizovaného vlastností (včetně `Default` vlastnosti).</span><span class="sxs-lookup"><span data-stu-id="cc425-141">Use parameterized properties (including `Default` properties).</span></span> <span data-ttu-id="cc425-142">Je potřeba deklarovat rozšířené vlastnosti za účelem zadejte parametr pro vlastnost, nebo k zadání dalších parametrů pro `Set` postupu.</span><span class="sxs-lookup"><span data-stu-id="cc425-142">You must declare an expanded property in order to specify a parameter for the property, or to specify additional parameters for the `Set` procedure.</span></span>  
  
-   <span data-ttu-id="cc425-143">Umístit na pole Základní atribut, nebo změnit úroveň přístupu tohoto pole zálohování.</span><span class="sxs-lookup"><span data-stu-id="cc425-143">Place an attribute on the backing field, or change the access level of the backing field.</span></span>  
  
-   <span data-ttu-id="cc425-144">Zadejte XML – komentáře pro pole zálohování.</span><span class="sxs-lookup"><span data-stu-id="cc425-144">Provide XML comments for the backing field.</span></span>  
  
## <a name="expanding-an-auto-implemented-property"></a><span data-ttu-id="cc425-145">Rozšíření ve automaticky implementované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="cc425-145">Expanding an Auto-Implemented Property</span></span>  
 <span data-ttu-id="cc425-146">Pokud máte ve automaticky implementované vlastnosti převést na rozšířené vlastnosti, která obsahuje `Get` nebo `Set` postupu editoru kódu jazyka Visual Basic může automaticky generovat `Get` a `Set` procedury a `End Property`příkaz Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cc425-146">If you have to convert an auto-implemented property to an expanded property that contains a `Get` or `Set` procedure, the Visual Basic Code Editor can automatically generate the `Get` and `Set` procedures and `End Property` statement for the property.</span></span> <span data-ttu-id="cc425-147">Pokud umístěte kurzor na prázdný řádek následující vygenerování kódu `Property` příkazu, zadejte `G` (pro `Get`) nebo `S` (pro `Set`) a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="cc425-147">The code is generated if you put the cursor on a blank line following the `Property` statement, type a `G` (for `Get`) or an `S` (for `Set`) and press ENTER.</span></span> <span data-ttu-id="cc425-148">Automaticky generuje editoru kódu jazyka Visual Basic `Get` nebo `Set` postup pro vlastnosti jen pro čtení a jen pro zápis po stisknutí klávesy ENTER na konci `Property` příkaz.</span><span class="sxs-lookup"><span data-stu-id="cc425-148">The Visual Basic Code Editor automatically generates the `Get` or `Set` procedure for read-only and write-only properties when you press ENTER at the end of a `Property` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc425-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc425-149">See Also</span></span>  
 [<span data-ttu-id="cc425-150">Postupy: deklarace a volání výchozí vlastnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cc425-150">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="cc425-151">Postupy: deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="cc425-151">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="cc425-152">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="cc425-152">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="cc425-153">Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cc425-153">ReadOnly</span></span>](../../../../visual-basic/language-reference/modifiers/readonly.md)  
 [<span data-ttu-id="cc425-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="cc425-154">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [<span data-ttu-id="cc425-155">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="cc425-155">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
