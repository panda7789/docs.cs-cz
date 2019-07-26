---
title: Datový typ objektu (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
ms.openlocfilehash: 1ac906494c49810e3d389591b1044f412e7320bc
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513052"
---
# <a name="object-data-type"></a><span data-ttu-id="8b612-102">Datový typ objektu</span><span class="sxs-lookup"><span data-stu-id="8b612-102">Object Data Type</span></span>

<span data-ttu-id="8b612-103">Obsahuje adresy, které odkazují na objekty.</span><span class="sxs-lookup"><span data-stu-id="8b612-103">Holds addresses that refer to objects.</span></span> <span data-ttu-id="8b612-104">`Object` Proměnné můžete přiřadit libovolný typ odkazu (řetězec, pole, třída nebo rozhraní).</span><span class="sxs-lookup"><span data-stu-id="8b612-104">You can assign any reference type (string, array, class, or interface) to an `Object` variable.</span></span> <span data-ttu-id="8b612-105">Proměnná může také odkazovat na data libovolného typu hodnoty ( `Char`číselná, `Boolean` `Date`,,, struktura nebo výčet). `Object`</span><span class="sxs-lookup"><span data-stu-id="8b612-105">An `Object` variable can also refer to data of any value type (numeric, `Boolean`, `Char`, `Date`, structure, or enumeration).</span></span>

## <a name="remarks"></a><span data-ttu-id="8b612-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b612-106">Remarks</span></span>

<span data-ttu-id="8b612-107">`Object` Datový typ může ukazovat na data libovolného datového typu, včetně jakékoli instance objektu, kterou vaše aplikace rozpoznává.</span><span class="sxs-lookup"><span data-stu-id="8b612-107">The `Object` data type can point to data of any data type, including any object instance your application recognizes.</span></span> <span data-ttu-id="8b612-108">Použijte `Object` , pokud v době kompilace neznáte, na jaký datový typ proměnné může odkazovat.</span><span class="sxs-lookup"><span data-stu-id="8b612-108">Use `Object` when you do not know at compile time what data type the variable might point to.</span></span>

<span data-ttu-id="8b612-109">Výchozí hodnota `Object` je `Nothing` (odkaz s hodnotou null).</span><span class="sxs-lookup"><span data-stu-id="8b612-109">The default value of `Object` is `Nothing` (a null reference).</span></span>

## <a name="data-types"></a><span data-ttu-id="8b612-110">Datové typy</span><span class="sxs-lookup"><span data-stu-id="8b612-110">Data Types</span></span>

<span data-ttu-id="8b612-111">Proměnné, konstanty nebo výrazy libovolného datového typu `Object` můžete přiřadit proměnné.</span><span class="sxs-lookup"><span data-stu-id="8b612-111">You can assign a variable, constant, or expression of any data type to an `Object` variable.</span></span> <span data-ttu-id="8b612-112">Chcete-li určit datový typ `Object` , na který proměnná aktuálně odkazuje, můžete <xref:System.Type.GetTypeCode%2A> použít metodu <xref:System.Type?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="8b612-112">To determine the data type an `Object` variable currently refers to, you can use the <xref:System.Type.GetTypeCode%2A> method of the <xref:System.Type?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="8b612-113">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="8b612-113">The following example illustrates this.</span></span>

```vb
Dim myObject As Object
' Suppose myObject has now had something assigned to it.
Dim datTyp As Integer
datTyp = Type.GetTypeCode(myObject.GetType())
```

<span data-ttu-id="8b612-114">`Object` Datový typ je odkazový typ.</span><span class="sxs-lookup"><span data-stu-id="8b612-114">The `Object` data type is a reference type.</span></span> <span data-ttu-id="8b612-115">Nicméně Visual Basic považuje `Object` proměnnou jako typ hodnoty, když odkazuje na data typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8b612-115">However, Visual Basic treats an `Object` variable as a value type when it refers to data of a value type.</span></span>

## <a name="storage"></a><span data-ttu-id="8b612-116">Úložiště</span><span class="sxs-lookup"><span data-stu-id="8b612-116">Storage</span></span>

<span data-ttu-id="8b612-117">Libovolný datový typ, na který odkazuje, `Object` proměnná neobsahuje datovou hodnotu samotnou, ale spíše ukazatel na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8b612-117">Whatever data type it refers to, an `Object` variable does not contain the data value itself, but rather a pointer to the value.</span></span> <span data-ttu-id="8b612-118">Vždycky používá čtyři bajty v paměti počítače, ale nezahrnuje úložiště dat, která představují hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="8b612-118">It always uses four bytes in computer memory, but this does not include the storage for the data representing the value of the variable.</span></span> <span data-ttu-id="8b612-119">Z důvodu kódu, který používá ukazatel k vyhledání dat, jsou proměnné `Object` , které mají typy hodnot, mírně pomalejší pro přístup, než explicitně typované proměnné.</span><span class="sxs-lookup"><span data-stu-id="8b612-119">Because of the code that uses the pointer to locate the data, `Object` variables holding value types are slightly slower to access than explicitly typed variables.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="8b612-120">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="8b612-120">Programming Tips</span></span>

- <span data-ttu-id="8b612-121">**Problematika spolupráce.**</span><span class="sxs-lookup"><span data-stu-id="8b612-121">**Interop Considerations.**</span></span> <span data-ttu-id="8b612-122">Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že typy ukazatelů v jiných prostředích nejsou kompatibilní s typem Visual Basic `Object` .</span><span class="sxs-lookup"><span data-stu-id="8b612-122">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that pointer types in other environments are not compatible with the Visual Basic `Object` type.</span></span>

- <span data-ttu-id="8b612-123">**Výkon.**</span><span class="sxs-lookup"><span data-stu-id="8b612-123">**Performance.**</span></span> <span data-ttu-id="8b612-124">Proměnná, kterou deklarujete s `Object` typem, je dostatečně flexibilní, aby obsahovala odkaz na libovolný objekt.</span><span class="sxs-lookup"><span data-stu-id="8b612-124">A variable you declare with the `Object` type is flexible enough to contain a reference to any object.</span></span> <span data-ttu-id="8b612-125">Nicméně pokud pro takovou proměnnou vyvoláte metodu nebo vlastnost, vždy se vám bude účtovat *pozdní vazba* (za běhu).</span><span class="sxs-lookup"><span data-stu-id="8b612-125">However, when you invoke a method or property on such a variable, you always incur *late binding* (at run time).</span></span> <span data-ttu-id="8b612-126">Chcete-li vynutit *počáteční vazbu* (v době kompilace) a lepší výkon, deklarujte proměnnou pomocí konkrétního názvu třídy nebo ji přetypujte na konkrétní datový typ.</span><span class="sxs-lookup"><span data-stu-id="8b612-126">To force *early binding* (at compile time) and better performance, declare the variable with a specific class name, or cast it to the specific data type.</span></span>

  <span data-ttu-id="8b612-127">Pokud deklarujete proměnnou objektu, zkuste použít konkrétní typ třídy, <xref:System.OperatingSystem>například namísto `Object` zobecněného typu.</span><span class="sxs-lookup"><span data-stu-id="8b612-127">When you declare an object variable, try to use a specific class type, for example <xref:System.OperatingSystem>, instead of the generalized `Object` type.</span></span> <span data-ttu-id="8b612-128">Měli byste také použít nejvíce dostupné třídy, <xref:System.Windows.Forms.TextBox> jako je například <xref:System.Windows.Forms.Control>namísto, abyste měli přístup k jeho vlastnostem a metodám.</span><span class="sxs-lookup"><span data-stu-id="8b612-128">You should also use the most specific class available, such as <xref:System.Windows.Forms.TextBox> instead of <xref:System.Windows.Forms.Control>, so that you can access its properties and methods.</span></span> <span data-ttu-id="8b612-129">Můžete obvykle použít seznam **třídy** v **Prohlížeč objektů** k vyhledání dostupných názvů tříd.</span><span class="sxs-lookup"><span data-stu-id="8b612-129">You can usually use the **Classes** list in the **Object Browser** to find available class names.</span></span>

- <span data-ttu-id="8b612-130">**Rozšiřující.**</span><span class="sxs-lookup"><span data-stu-id="8b612-130">**Widening.**</span></span> <span data-ttu-id="8b612-131">Všechny datové typy a všechny typy odkazů se rozšíří na `Object` datový typ.</span><span class="sxs-lookup"><span data-stu-id="8b612-131">All data types and all reference types widen to the `Object` data type.</span></span> <span data-ttu-id="8b612-132">To znamená, že můžete převést libovolný typ `Object` na bez výskytu <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="8b612-132">This means you can convert any type to `Object` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

  <span data-ttu-id="8b612-133">Nicméně pokud převedete mezi typy hodnot a `Object`, Visual Basic provádí operace s názvem zabalení a rozbalení, které provádějí zpracování pomaleji.</span><span class="sxs-lookup"><span data-stu-id="8b612-133">However, if you convert between value types and `Object`, Visual Basic performs operations called *boxing* and *unboxing*, which make execution slower.</span></span>

- <span data-ttu-id="8b612-134">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="8b612-134">**Type Characters.**</span></span> <span data-ttu-id="8b612-135">`Object`nemá žádný znak typu literálu nebo znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="8b612-135">`Object` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="8b612-136">**Typ rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="8b612-136">**Framework Type.**</span></span> <span data-ttu-id="8b612-137">Odpovídající typ v .NET Framework je <xref:System.Object?displayProperty=nameWithType> třída.</span><span class="sxs-lookup"><span data-stu-id="8b612-137">The corresponding type in the .NET Framework is the <xref:System.Object?displayProperty=nameWithType> class.</span></span>

## <a name="example"></a><span data-ttu-id="8b612-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="8b612-138">Example</span></span>

<span data-ttu-id="8b612-139">Následující příklad ukazuje `Object` proměnnou odkazující na instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="8b612-139">The following example illustrates an `Object` variable pointing to an object instance.</span></span>

```vb
Dim objDb As Object
Dim myCollection As New Collection()
' Suppose myCollection has now been populated.
objDb = myCollection.Item(1)
```

## <a name="see-also"></a><span data-ttu-id="8b612-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b612-140">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="8b612-141">Datové typy</span><span class="sxs-lookup"><span data-stu-id="8b612-141">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="8b612-142">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="8b612-142">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="8b612-143">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="8b612-143">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="8b612-144">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="8b612-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="8b612-145">Postupy: Určení, zda dva objekty souvisejí</span><span class="sxs-lookup"><span data-stu-id="8b612-145">How to: Determine Whether Two Objects Are Related</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="8b612-146">Postupy: Určení, zda jsou dva objekty identické</span><span class="sxs-lookup"><span data-stu-id="8b612-146">How to: Determine Whether Two Objects Are Identical</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
