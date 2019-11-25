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
ms.openlocfilehash: b322bd2215c95298be0a33ace1f3590a63878e24
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350387"
---
# <a name="auto-implemented-properties-visual-basic"></a><span data-ttu-id="03a7e-102">Automaticky implementované vlastnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03a7e-102">Auto-Implemented Properties (Visual Basic)</span></span>
<span data-ttu-id="03a7e-103">*Auto-implemented properties* enable you to quickly specify a property of a class without having to write code to `Get` and `Set` the property.</span><span class="sxs-lookup"><span data-stu-id="03a7e-103">*Auto-implemented properties* enable you to quickly specify a property of a class without having to write code to `Get` and `Set` the property.</span></span> <span data-ttu-id="03a7e-104">When you write code for an auto-implemented property, the Visual Basic compiler automatically creates a private field to store the property variable in addition to creating the associated `Get` and `Set` procedures.</span><span class="sxs-lookup"><span data-stu-id="03a7e-104">When you write code for an auto-implemented property, the Visual Basic compiler automatically creates a private field to store the property variable in addition to creating the associated `Get` and `Set` procedures.</span></span>  
  
 <span data-ttu-id="03a7e-105">With auto-implemented properties, a property, including a default value, can be declared in a single line.</span><span class="sxs-lookup"><span data-stu-id="03a7e-105">With auto-implemented properties, a property, including a default value, can be declared in a single line.</span></span> <span data-ttu-id="03a7e-106">The following example shows three property declarations.</span><span class="sxs-lookup"><span data-stu-id="03a7e-106">The following example shows three property declarations.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#1)]  
  
 <span data-ttu-id="03a7e-107">An auto-implemented property is equivalent to a property for which the property value is stored in a private field.</span><span class="sxs-lookup"><span data-stu-id="03a7e-107">An auto-implemented property is equivalent to a property for which the property value is stored in a private field.</span></span> <span data-ttu-id="03a7e-108">The following code example shows an auto-implemented property.</span><span class="sxs-lookup"><span data-stu-id="03a7e-108">The following code example shows an auto-implemented property.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#5)]  
  
 <span data-ttu-id="03a7e-109">The following code example shows the equivalent code for the previous auto-implemented property example.</span><span class="sxs-lookup"><span data-stu-id="03a7e-109">The following code example shows the equivalent code for the previous auto-implemented property example.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#2)]  
  
 <span data-ttu-id="03a7e-110">The following code show implementing readonly properties:</span><span class="sxs-lookup"><span data-stu-id="03a7e-110">The following code show implementing readonly properties:</span></span>  
  
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
  
 <span data-ttu-id="03a7e-111">You can assign to the property with initialization expressions as shown in the example, or you can assign to the properties in the containing type’s constructor.</span><span class="sxs-lookup"><span data-stu-id="03a7e-111">You can assign to the property with initialization expressions as shown in the example, or you can assign to the properties in the containing type’s constructor.</span></span>  <span data-ttu-id="03a7e-112">You can assign to the backing fields of readonly properties at any time.</span><span class="sxs-lookup"><span data-stu-id="03a7e-112">You can assign to the backing fields of readonly properties at any time.</span></span>  
  
## <a name="backing-field"></a><span data-ttu-id="03a7e-113">Backing Field</span><span class="sxs-lookup"><span data-stu-id="03a7e-113">Backing Field</span></span>  
 <span data-ttu-id="03a7e-114">When you declare an auto-implemented property, Visual Basic automatically creates a hidden private field called the *backing field* to contain the property value.</span><span class="sxs-lookup"><span data-stu-id="03a7e-114">When you declare an auto-implemented property, Visual Basic automatically creates a hidden private field called the *backing field* to contain the property value.</span></span> <span data-ttu-id="03a7e-115">The backing field name is the auto-implemented property name preceded by an underscore (_).</span><span class="sxs-lookup"><span data-stu-id="03a7e-115">The backing field name is the auto-implemented property name preceded by an underscore (_).</span></span> <span data-ttu-id="03a7e-116">For example, if you declare an auto-implemented property named `ID`, the backing field is named `_ID`.</span><span class="sxs-lookup"><span data-stu-id="03a7e-116">For example, if you declare an auto-implemented property named `ID`, the backing field is named `_ID`.</span></span> <span data-ttu-id="03a7e-117">If you include a member of your class that is also named `_ID`, you produce a naming conflict and Visual Basic reports a compiler error.</span><span class="sxs-lookup"><span data-stu-id="03a7e-117">If you include a member of your class that is also named `_ID`, you produce a naming conflict and Visual Basic reports a compiler error.</span></span>  
  
 <span data-ttu-id="03a7e-118">The backing field also has the following characteristics:</span><span class="sxs-lookup"><span data-stu-id="03a7e-118">The backing field also has the following characteristics:</span></span>  
  
- <span data-ttu-id="03a7e-119">The access modifier for the backing field is always `Private`, even when the property itself has a different access level, such as `Public`.</span><span class="sxs-lookup"><span data-stu-id="03a7e-119">The access modifier for the backing field is always `Private`, even when the property itself has a different access level, such as `Public`.</span></span>  
  
- <span data-ttu-id="03a7e-120">If the property is marked as `Shared`, the backing field also is shared.</span><span class="sxs-lookup"><span data-stu-id="03a7e-120">If the property is marked as `Shared`, the backing field also is shared.</span></span>  
  
- <span data-ttu-id="03a7e-121">Attributes specified for the property do not apply to the backing field.</span><span class="sxs-lookup"><span data-stu-id="03a7e-121">Attributes specified for the property do not apply to the backing field.</span></span>  
  
- <span data-ttu-id="03a7e-122">The backing field can be accessed from code within the class and from debugging tools such as the Watch window.</span><span class="sxs-lookup"><span data-stu-id="03a7e-122">The backing field can be accessed from code within the class and from debugging tools such as the Watch window.</span></span> <span data-ttu-id="03a7e-123">However, the backing field does not show in an IntelliSense word completion list.</span><span class="sxs-lookup"><span data-stu-id="03a7e-123">However, the backing field does not show in an IntelliSense word completion list.</span></span>  
  
## <a name="initializing-an-auto-implemented-property"></a><span data-ttu-id="03a7e-124">Initializing an Auto-Implemented Property</span><span class="sxs-lookup"><span data-stu-id="03a7e-124">Initializing an Auto-Implemented Property</span></span>  
 <span data-ttu-id="03a7e-125">Any expression that can be used to initialize a field is valid for initializing an auto-implemented property.</span><span class="sxs-lookup"><span data-stu-id="03a7e-125">Any expression that can be used to initialize a field is valid for initializing an auto-implemented property.</span></span> <span data-ttu-id="03a7e-126">When you initialize an auto-implemented property, the expression is evaluated and passed to the `Set` procedure for the property.</span><span class="sxs-lookup"><span data-stu-id="03a7e-126">When you initialize an auto-implemented property, the expression is evaluated and passed to the `Set` procedure for the property.</span></span> <span data-ttu-id="03a7e-127">The following code examples show some auto-implemented properties that include initial values.</span><span class="sxs-lookup"><span data-stu-id="03a7e-127">The following code examples show some auto-implemented properties that include initial values.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 <span data-ttu-id="03a7e-128">You cannot initialize an auto-implemented property that is a member of an `Interface`, or one that is marked `MustOverride`.</span><span class="sxs-lookup"><span data-stu-id="03a7e-128">You cannot initialize an auto-implemented property that is a member of an `Interface`, or one that is marked `MustOverride`.</span></span>  
  
 <span data-ttu-id="03a7e-129">When you declare an auto-implemented property as a member of a `Structure`, you can only initialize the auto-implemented property if it is marked as `Shared`.</span><span class="sxs-lookup"><span data-stu-id="03a7e-129">When you declare an auto-implemented property as a member of a `Structure`, you can only initialize the auto-implemented property if it is marked as `Shared`.</span></span>  
  
 <span data-ttu-id="03a7e-130">When you declare an auto-implemented property as an array, you cannot specify explicit array bounds.</span><span class="sxs-lookup"><span data-stu-id="03a7e-130">When you declare an auto-implemented property as an array, you cannot specify explicit array bounds.</span></span> <span data-ttu-id="03a7e-131">However, you can supply a value by using an array initializer, as shown in the following examples.</span><span class="sxs-lookup"><span data-stu-id="03a7e-131">However, you can supply a value by using an array initializer, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a><span data-ttu-id="03a7e-132">Property Definitions That Require Standard Syntax</span><span class="sxs-lookup"><span data-stu-id="03a7e-132">Property Definitions That Require Standard Syntax</span></span>  
 <span data-ttu-id="03a7e-133">Auto-implemented properties are convenient and support many programming scenarios.</span><span class="sxs-lookup"><span data-stu-id="03a7e-133">Auto-implemented properties are convenient and support many programming scenarios.</span></span> <span data-ttu-id="03a7e-134">However, there are situations in which you cannot use an auto-implemented property and must instead use standard, or *expanded*, property syntax.</span><span class="sxs-lookup"><span data-stu-id="03a7e-134">However, there are situations in which you cannot use an auto-implemented property and must instead use standard, or *expanded*, property syntax.</span></span>  
  
 <span data-ttu-id="03a7e-135">You have to use expanded property-definition syntax if you want to do any one of the following:</span><span class="sxs-lookup"><span data-stu-id="03a7e-135">You have to use expanded property-definition syntax if you want to do any one of the following:</span></span>  
  
- <span data-ttu-id="03a7e-136">Add code to the `Get` or `Set` procedure of a property, such as code to validate incoming values in the `Set` procedure.</span><span class="sxs-lookup"><span data-stu-id="03a7e-136">Add code to the `Get` or `Set` procedure of a property, such as code to validate incoming values in the `Set` procedure.</span></span> <span data-ttu-id="03a7e-137">For example, you might want to verify that a string that represents a telephone number contains the required number of numerals before setting the property value.</span><span class="sxs-lookup"><span data-stu-id="03a7e-137">For example, you might want to verify that a string that represents a telephone number contains the required number of numerals before setting the property value.</span></span>  
  
- <span data-ttu-id="03a7e-138">Specify different accessibility for the `Get` and `Set` procedure.</span><span class="sxs-lookup"><span data-stu-id="03a7e-138">Specify different accessibility for the `Get` and `Set` procedure.</span></span> <span data-ttu-id="03a7e-139">For example, you might want to make the `Set` procedure `Private` and the `Get` procedure `Public`.</span><span class="sxs-lookup"><span data-stu-id="03a7e-139">For example, you might want to make the `Set` procedure `Private` and the `Get` procedure `Public`.</span></span>  
  
- <span data-ttu-id="03a7e-140">Create properties that are `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="03a7e-140">Create properties that are `WriteOnly`.</span></span>  
  
- <span data-ttu-id="03a7e-141">Use parameterized properties (including `Default` properties).</span><span class="sxs-lookup"><span data-stu-id="03a7e-141">Use parameterized properties (including `Default` properties).</span></span> <span data-ttu-id="03a7e-142">You must declare an expanded property in order to specify a parameter for the property, or to specify additional parameters for the `Set` procedure.</span><span class="sxs-lookup"><span data-stu-id="03a7e-142">You must declare an expanded property in order to specify a parameter for the property, or to specify additional parameters for the `Set` procedure.</span></span>  
  
- <span data-ttu-id="03a7e-143">Place an attribute on the backing field, or change the access level of the backing field.</span><span class="sxs-lookup"><span data-stu-id="03a7e-143">Place an attribute on the backing field, or change the access level of the backing field.</span></span>  
  
- <span data-ttu-id="03a7e-144">Provide XML comments for the backing field.</span><span class="sxs-lookup"><span data-stu-id="03a7e-144">Provide XML comments for the backing field.</span></span>  
  
## <a name="expanding-an-auto-implemented-property"></a><span data-ttu-id="03a7e-145">Expanding an Auto-Implemented Property</span><span class="sxs-lookup"><span data-stu-id="03a7e-145">Expanding an Auto-Implemented Property</span></span>  
 <span data-ttu-id="03a7e-146">If you have to convert an auto-implemented property to an expanded property that contains a `Get` or `Set` procedure, the Visual Basic Code Editor can automatically generate the `Get` and `Set` procedures and `End Property` statement for the property.</span><span class="sxs-lookup"><span data-stu-id="03a7e-146">If you have to convert an auto-implemented property to an expanded property that contains a `Get` or `Set` procedure, the Visual Basic Code Editor can automatically generate the `Get` and `Set` procedures and `End Property` statement for the property.</span></span> <span data-ttu-id="03a7e-147">The code is generated if you put the cursor on a blank line following the `Property` statement, type a `G` (for `Get`) or an `S` (for `Set`) and press ENTER.</span><span class="sxs-lookup"><span data-stu-id="03a7e-147">The code is generated if you put the cursor on a blank line following the `Property` statement, type a `G` (for `Get`) or an `S` (for `Set`) and press ENTER.</span></span> <span data-ttu-id="03a7e-148">The Visual Basic Code Editor automatically generates the `Get` or `Set` procedure for read-only and write-only properties when you press ENTER at the end of a `Property` statement.</span><span class="sxs-lookup"><span data-stu-id="03a7e-148">The Visual Basic Code Editor automatically generates the `Get` or `Set` procedure for read-only and write-only properties when you press ENTER at the end of a `Property` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03a7e-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03a7e-149">See also</span></span>

- [<span data-ttu-id="03a7e-150">How to: Declare and Call a Default Property in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="03a7e-150">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="03a7e-151">Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="03a7e-151">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="03a7e-152">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="03a7e-152">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="03a7e-153">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="03a7e-153">ReadOnly</span></span>](../../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="03a7e-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="03a7e-154">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="03a7e-155">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="03a7e-155">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
