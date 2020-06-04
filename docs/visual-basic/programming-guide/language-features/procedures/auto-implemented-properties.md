---
title: Automaticky implementované vlastnosti
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: d991a385e537c43daeb708e96e712acd92110379
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403379"
---
# <a name="auto-implemented-properties-visual-basic"></a><span data-ttu-id="2670f-102">Automaticky implementované vlastnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2670f-102">Auto-Implemented Properties (Visual Basic)</span></span>
<span data-ttu-id="2670f-103">*Automaticky implementované vlastnosti* umožňují rychle zadat vlastnost třídy bez nutnosti psát kód do `Get` a `Set` Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2670f-103">*Auto-implemented properties* enable you to quickly specify a property of a class without having to write code to `Get` and `Set` the property.</span></span> <span data-ttu-id="2670f-104">Při psaní kódu pro automaticky implementovanou vlastnost automaticky vytvoří kompilátor Visual Basic privátní pole pro uložení proměnné vlastnosti kromě vytvoření přidružených `Get` a `Set` postupů.</span><span class="sxs-lookup"><span data-stu-id="2670f-104">When you write code for an auto-implemented property, the Visual Basic compiler automatically creates a private field to store the property variable in addition to creating the associated `Get` and `Set` procedures.</span></span>  
  
 <span data-ttu-id="2670f-105">S automaticky implementovanými vlastnostmi lze vlastnost, včetně výchozí hodnoty, deklarovat na jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="2670f-105">With auto-implemented properties, a property, including a default value, can be declared in a single line.</span></span> <span data-ttu-id="2670f-106">Následující příklad ukazuje tři deklarace vlastností.</span><span class="sxs-lookup"><span data-stu-id="2670f-106">The following example shows three property declarations.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#1)]  
  
 <span data-ttu-id="2670f-107">Automaticky implementovaná vlastnost je ekvivalentní vlastnosti, pro kterou je hodnota vlastnosti uložena v soukromém poli.</span><span class="sxs-lookup"><span data-stu-id="2670f-107">An auto-implemented property is equivalent to a property for which the property value is stored in a private field.</span></span> <span data-ttu-id="2670f-108">Následující příklad kódu ukazuje automaticky implementovanou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2670f-108">The following code example shows an auto-implemented property.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#5)]  
  
 <span data-ttu-id="2670f-109">Následující příklad kódu ukazuje ekvivalentní kód pro předchozí automaticky implementovaný příklad vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2670f-109">The following code example shows the equivalent code for the previous auto-implemented property example.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#2)]  
  
 <span data-ttu-id="2670f-110">Následující kód ukazuje implementaci vlastností ReadOnly:</span><span class="sxs-lookup"><span data-stu-id="2670f-110">The following code show implementing readonly properties:</span></span>  
  
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
  
 <span data-ttu-id="2670f-111">K vlastnosti můžete přiřadit výrazy inicializace, jak je znázorněno v příkladu, nebo můžete přiřadit vlastnosti v konstruktoru nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="2670f-111">You can assign to the property with initialization expressions as shown in the example, or you can assign to the properties in the containing type’s constructor.</span></span>  <span data-ttu-id="2670f-112">Můžete kdykoli přiřadit k zálohovaným polím vlastností ReadOnly.</span><span class="sxs-lookup"><span data-stu-id="2670f-112">You can assign to the backing fields of readonly properties at any time.</span></span>  
  
## <a name="backing-field"></a><span data-ttu-id="2670f-113">Pole pro zálohování</span><span class="sxs-lookup"><span data-stu-id="2670f-113">Backing Field</span></span>  
 <span data-ttu-id="2670f-114">Pokud deklarujete automaticky implementovanou vlastnost, Visual Basic automaticky vytvoří skryté soukromé pole s názvem *pole zálohování* , které obsahuje hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2670f-114">When you declare an auto-implemented property, Visual Basic automatically creates a hidden private field called the *backing field* to contain the property value.</span></span> <span data-ttu-id="2670f-115">Název záložního pole je název automaticky implementované vlastnosti předchází podtržítkem (_).</span><span class="sxs-lookup"><span data-stu-id="2670f-115">The backing field name is the auto-implemented property name preceded by an underscore (_).</span></span> <span data-ttu-id="2670f-116">Například pokud deklarujete automaticky implementovanou vlastnost s názvem `ID` , pole pro zálohování je pojmenované `_ID` .</span><span class="sxs-lookup"><span data-stu-id="2670f-116">For example, if you declare an auto-implemented property named `ID`, the backing field is named `_ID`.</span></span> <span data-ttu-id="2670f-117">Pokud zahrnete člena vaší třídy, která je také pojmenována `_ID` , dojde k vytvoření konfliktu pojmenování a Visual Basic hlásí chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="2670f-117">If you include a member of your class that is also named `_ID`, you produce a naming conflict and Visual Basic reports a compiler error.</span></span>  
  
 <span data-ttu-id="2670f-118">Pole pro zálohování má také následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="2670f-118">The backing field also has the following characteristics:</span></span>  
  
- <span data-ttu-id="2670f-119">Modifikátor přístupu pro pole pro zálohování je vždy `Private` , i když má sama vlastnost jinou úroveň přístupu, například `Public` .</span><span class="sxs-lookup"><span data-stu-id="2670f-119">The access modifier for the backing field is always `Private`, even when the property itself has a different access level, such as `Public`.</span></span>  
  
- <span data-ttu-id="2670f-120">Je-li vlastnost označena jako `Shared` , je sdíleno také pole zálohování.</span><span class="sxs-lookup"><span data-stu-id="2670f-120">If the property is marked as `Shared`, the backing field also is shared.</span></span>  
  
- <span data-ttu-id="2670f-121">Atributy zadané pro vlastnost se nevztahují na pole pro zálohování.</span><span class="sxs-lookup"><span data-stu-id="2670f-121">Attributes specified for the property do not apply to the backing field.</span></span>  
  
- <span data-ttu-id="2670f-122">K poli pro zálohování se dá dostat z kódu v rámci třídy a z ladicích nástrojů, jako je okno Kukátko.</span><span class="sxs-lookup"><span data-stu-id="2670f-122">The backing field can be accessed from code within the class and from debugging tools such as the Watch window.</span></span> <span data-ttu-id="2670f-123">Pole zálohování se ale nezobrazí v seznamu dokončování slov IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="2670f-123">However, the backing field does not show in an IntelliSense word completion list.</span></span>  
  
## <a name="initializing-an-auto-implemented-property"></a><span data-ttu-id="2670f-124">Inicializuje se automaticky implementovaná vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2670f-124">Initializing an Auto-Implemented Property</span></span>  
 <span data-ttu-id="2670f-125">Libovolný výraz, který lze použít k inicializaci pole, je platný pro inicializaci automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2670f-125">Any expression that can be used to initialize a field is valid for initializing an auto-implemented property.</span></span> <span data-ttu-id="2670f-126">Při inicializaci automaticky implementované vlastnosti je výraz vyhodnocen a předán do `Set` procedury pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2670f-126">When you initialize an auto-implemented property, the expression is evaluated and passed to the `Set` procedure for the property.</span></span> <span data-ttu-id="2670f-127">Následující příklady kódu ukazují některé automaticky implementované vlastnosti, které obsahují počáteční hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2670f-127">The following code examples show some auto-implemented properties that include initial values.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 <span data-ttu-id="2670f-128">Nelze inicializovat automaticky implementovanou vlastnost, která je členem třídy `Interface` nebo která je označena jako `MustOverride` .</span><span class="sxs-lookup"><span data-stu-id="2670f-128">You cannot initialize an auto-implemented property that is a member of an `Interface`, or one that is marked `MustOverride`.</span></span>  
  
 <span data-ttu-id="2670f-129">Pokud deklarujete automaticky implementovanou vlastnost jako člen a `Structure` , můžete pouze inicializovat automaticky implementovanou vlastnost, pokud je označena jako `Shared` .</span><span class="sxs-lookup"><span data-stu-id="2670f-129">When you declare an auto-implemented property as a member of a `Structure`, you can only initialize the auto-implemented property if it is marked as `Shared`.</span></span>  
  
 <span data-ttu-id="2670f-130">Pokud deklarujete automaticky implementovanou vlastnost jako pole, nemůžete zadat explicitní meze pole.</span><span class="sxs-lookup"><span data-stu-id="2670f-130">When you declare an auto-implemented property as an array, you cannot specify explicit array bounds.</span></span> <span data-ttu-id="2670f-131">Můžete však dodat hodnotu pomocí inicializátoru pole, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="2670f-131">However, you can supply a value by using an array initializer, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a><span data-ttu-id="2670f-132">Definice vlastností, které vyžadují standardní syntaxi</span><span class="sxs-lookup"><span data-stu-id="2670f-132">Property Definitions That Require Standard Syntax</span></span>  
 <span data-ttu-id="2670f-133">Automaticky implementované vlastnosti jsou pohodlné a podporují řadu programovacích scénářů.</span><span class="sxs-lookup"><span data-stu-id="2670f-133">Auto-implemented properties are convenient and support many programming scenarios.</span></span> <span data-ttu-id="2670f-134">Existují však situace, kdy nemůžete použít automaticky implementovanou vlastnost a místo toho je třeba použít standardní nebo *rozbalenou*syntaxi vlastností.</span><span class="sxs-lookup"><span data-stu-id="2670f-134">However, there are situations in which you cannot use an auto-implemented property and must instead use standard, or *expanded*, property syntax.</span></span>  
  
 <span data-ttu-id="2670f-135">Pokud chcete provést některou z následujících akcí, je nutné použít rozšířenou syntaxi definice vlastností:</span><span class="sxs-lookup"><span data-stu-id="2670f-135">You have to use expanded property-definition syntax if you want to do any one of the following:</span></span>  
  
- <span data-ttu-id="2670f-136">Přidejte kód do `Get` procedury nebo pro `Set` vlastnost, jako je například kód pro ověření příchozích hodnot v `Set` proceduře.</span><span class="sxs-lookup"><span data-stu-id="2670f-136">Add code to the `Get` or `Set` procedure of a property, such as code to validate incoming values in the `Set` procedure.</span></span> <span data-ttu-id="2670f-137">Například může být vhodné ověřit, že řetězec představující telefonní číslo obsahuje požadovaný počet číslic před nastavením hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2670f-137">For example, you might want to verify that a string that represents a telephone number contains the required number of numerals before setting the property value.</span></span>  
  
- <span data-ttu-id="2670f-138">Zadejte pro `Get` proceduru a jinou přístupnost `Set` .</span><span class="sxs-lookup"><span data-stu-id="2670f-138">Specify different accessibility for the `Get` and `Set` procedure.</span></span> <span data-ttu-id="2670f-139">Například může být vhodné provést `Set` postup `Private` a `Get` postup `Public` .</span><span class="sxs-lookup"><span data-stu-id="2670f-139">For example, you might want to make the `Set` procedure `Private` and the `Get` procedure `Public`.</span></span>  
  
- <span data-ttu-id="2670f-140">Vytvořte vlastnosti, které jsou `WriteOnly` .</span><span class="sxs-lookup"><span data-stu-id="2670f-140">Create properties that are `WriteOnly`.</span></span>  
  
- <span data-ttu-id="2670f-141">Použijte parametrizované vlastnosti (včetně `Default` vlastností).</span><span class="sxs-lookup"><span data-stu-id="2670f-141">Use parameterized properties (including `Default` properties).</span></span> <span data-ttu-id="2670f-142">Aby bylo možné zadat parametr pro vlastnost nebo zadat další parametry pro proceduru, je nutné deklarovat rozšířenou vlastnost `Set` .</span><span class="sxs-lookup"><span data-stu-id="2670f-142">You must declare an expanded property in order to specify a parameter for the property, or to specify additional parameters for the `Set` procedure.</span></span>  
  
- <span data-ttu-id="2670f-143">Umístěte atribut do pole zálohování nebo změňte úroveň přístupu v poli pro zálohování.</span><span class="sxs-lookup"><span data-stu-id="2670f-143">Place an attribute on the backing field, or change the access level of the backing field.</span></span>  
  
- <span data-ttu-id="2670f-144">Zadejte komentáře XML pro pole zálohování.</span><span class="sxs-lookup"><span data-stu-id="2670f-144">Provide XML comments for the backing field.</span></span>  
  
## <a name="expanding-an-auto-implemented-property"></a><span data-ttu-id="2670f-145">Rozšíření automaticky implementované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2670f-145">Expanding an Auto-Implemented Property</span></span>  
 <span data-ttu-id="2670f-146">Pokud je nutné převést automaticky implementovanou vlastnost na rozšířenou vlastnost, která obsahuje `Get` `Set` proceduru or, Editor kódu Visual Basic může automaticky generovat `Get` `Set` procedury a `End Property` příkazy pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2670f-146">If you have to convert an auto-implemented property to an expanded property that contains a `Get` or `Set` procedure, the Visual Basic Code Editor can automatically generate the `Get` and `Set` procedures and `End Property` statement for the property.</span></span> <span data-ttu-id="2670f-147">Kód je generován při vložení kurzoru do prázdného řádku po `Property` příkazu, zadejte a `G` (pro `Get` ) nebo `S` (pro `Set` ) a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="2670f-147">The code is generated if you put the cursor on a blank line following the `Property` statement, type a `G` (for `Get`) or an `S` (for `Set`) and press ENTER.</span></span> <span data-ttu-id="2670f-148">Editor kódu Visual Basic automaticky generuje `Get` `Set` proceduru nebo pro vlastnosti jen pro čtení a jen pro zápis při stisknutí klávesy ENTER na konci `Property` příkazu.</span><span class="sxs-lookup"><span data-stu-id="2670f-148">The Visual Basic Code Editor automatically generates the `Get` or `Set` procedure for read-only and write-only properties when you press ENTER at the end of a `Property` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2670f-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="2670f-149">See also</span></span>

- [<span data-ttu-id="2670f-150">Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2670f-150">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="2670f-151">Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="2670f-151">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="2670f-152">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="2670f-152">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="2670f-153">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="2670f-153">ReadOnly</span></span>](../../../language-reference/modifiers/readonly.md)
- [<span data-ttu-id="2670f-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="2670f-154">WriteOnly</span></span>](../../../language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="2670f-155">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="2670f-155">Objects and Classes</span></span>](../objects-and-classes/index.md)
