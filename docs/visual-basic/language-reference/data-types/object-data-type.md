---
title: Datový typ objektu
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
ms.openlocfilehash: 14770e74a0169dba3a45a04845dd32323e6201e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415580"
---
# <a name="object-data-type"></a><span data-ttu-id="54bf8-102">Datový typ objektu</span><span class="sxs-lookup"><span data-stu-id="54bf8-102">Object Data Type</span></span>

<span data-ttu-id="54bf8-103">Obsahuje adresy, které odkazují na objekty.</span><span class="sxs-lookup"><span data-stu-id="54bf8-103">Holds addresses that refer to objects.</span></span> <span data-ttu-id="54bf8-104">Proměnné můžete přiřadit libovolný typ odkazu (řetězec, pole, třída nebo rozhraní) `Object` .</span><span class="sxs-lookup"><span data-stu-id="54bf8-104">You can assign any reference type (string, array, class, or interface) to an `Object` variable.</span></span> <span data-ttu-id="54bf8-105">`Object`Proměnná může také odkazovat na data libovolného typu hodnoty (číselná,,, `Boolean` `Char` `Date` , struktura nebo výčet).</span><span class="sxs-lookup"><span data-stu-id="54bf8-105">An `Object` variable can also refer to data of any value type (numeric, `Boolean`, `Char`, `Date`, structure, or enumeration).</span></span>

## <a name="remarks"></a><span data-ttu-id="54bf8-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="54bf8-106">Remarks</span></span>

<span data-ttu-id="54bf8-107">`Object`Datový typ může ukazovat na data libovolného datového typu, včetně jakékoli instance objektu, kterou vaše aplikace rozpoznává.</span><span class="sxs-lookup"><span data-stu-id="54bf8-107">The `Object` data type can point to data of any data type, including any object instance your application recognizes.</span></span> <span data-ttu-id="54bf8-108">Použijte, `Object` Pokud v době kompilace neznáte, na jaký datový typ proměnné může odkazovat.</span><span class="sxs-lookup"><span data-stu-id="54bf8-108">Use `Object` when you do not know at compile time what data type the variable might point to.</span></span>

<span data-ttu-id="54bf8-109">Výchozí hodnota `Object` je `Nothing` (odkaz s hodnotou null).</span><span class="sxs-lookup"><span data-stu-id="54bf8-109">The default value of `Object` is `Nothing` (a null reference).</span></span>

## <a name="data-types"></a><span data-ttu-id="54bf8-110">Typy dat</span><span class="sxs-lookup"><span data-stu-id="54bf8-110">Data Types</span></span>

<span data-ttu-id="54bf8-111">Proměnné, konstanty nebo výrazy libovolného datového typu můžete přiřadit `Object` proměnné.</span><span class="sxs-lookup"><span data-stu-id="54bf8-111">You can assign a variable, constant, or expression of any data type to an `Object` variable.</span></span> <span data-ttu-id="54bf8-112">Chcete-li určit datový typ `Object` , na který proměnná aktuálně odkazuje, můžete použít <xref:System.Type.GetTypeCode%2A> metodu <xref:System.Type?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="54bf8-112">To determine the data type an `Object` variable currently refers to, you can use the <xref:System.Type.GetTypeCode%2A> method of the <xref:System.Type?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="54bf8-113">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="54bf8-113">The following example illustrates this.</span></span>

```vb
Dim myObject As Object
' Suppose myObject has now had something assigned to it.
Dim datTyp As Integer
datTyp = Type.GetTypeCode(myObject.GetType())
```

<span data-ttu-id="54bf8-114">`Object`Datový typ je odkazový typ.</span><span class="sxs-lookup"><span data-stu-id="54bf8-114">The `Object` data type is a reference type.</span></span> <span data-ttu-id="54bf8-115">Nicméně Visual Basic považuje `Object` proměnnou jako typ hodnoty, když odkazuje na data typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="54bf8-115">However, Visual Basic treats an `Object` variable as a value type when it refers to data of a value type.</span></span>

## <a name="storage"></a><span data-ttu-id="54bf8-116">Storage</span><span class="sxs-lookup"><span data-stu-id="54bf8-116">Storage</span></span>

<span data-ttu-id="54bf8-117">Libovolný datový typ, na který odkazuje, `Object` Proměnná neobsahuje datovou hodnotu samotnou, ale spíše ukazatel na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="54bf8-117">Whatever data type it refers to, an `Object` variable does not contain the data value itself, but rather a pointer to the value.</span></span> <span data-ttu-id="54bf8-118">Vždycky používá čtyři bajty v paměti počítače, ale nezahrnuje úložiště dat, která představují hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="54bf8-118">It always uses four bytes in computer memory, but this does not include the storage for the data representing the value of the variable.</span></span> <span data-ttu-id="54bf8-119">Z důvodu kódu, který používá ukazatel k vyhledání dat, jsou proměnné, které mají `Object` typy hodnot, mírně pomalejší pro přístup, než explicitně typované proměnné.</span><span class="sxs-lookup"><span data-stu-id="54bf8-119">Because of the code that uses the pointer to locate the data, `Object` variables holding value types are slightly slower to access than explicitly typed variables.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="54bf8-120">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="54bf8-120">Programming Tips</span></span>

- <span data-ttu-id="54bf8-121">**Problematika spolupráce.**</span><span class="sxs-lookup"><span data-stu-id="54bf8-121">**Interop Considerations.**</span></span> <span data-ttu-id="54bf8-122">Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že typy ukazatelů v jiných prostředích nejsou kompatibilní s typem Visual Basic `Object` .</span><span class="sxs-lookup"><span data-stu-id="54bf8-122">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that pointer types in other environments are not compatible with the Visual Basic `Object` type.</span></span>

- <span data-ttu-id="54bf8-123">**Předepsané.**</span><span class="sxs-lookup"><span data-stu-id="54bf8-123">**Performance.**</span></span> <span data-ttu-id="54bf8-124">Proměnná, kterou deklarujete s `Object` typem, je dostatečně flexibilní, aby obsahovala odkaz na libovolný objekt.</span><span class="sxs-lookup"><span data-stu-id="54bf8-124">A variable you declare with the `Object` type is flexible enough to contain a reference to any object.</span></span> <span data-ttu-id="54bf8-125">Nicméně pokud pro takovou proměnnou vyvoláte metodu nebo vlastnost, vždy se vám bude účtovat *pozdní vazba* (za běhu).</span><span class="sxs-lookup"><span data-stu-id="54bf8-125">However, when you invoke a method or property on such a variable, you always incur *late binding* (at run time).</span></span> <span data-ttu-id="54bf8-126">Chcete-li vynutit *počáteční vazbu* (v době kompilace) a lepší výkon, deklarujte proměnnou pomocí konkrétního názvu třídy nebo ji přetypujte na konkrétní datový typ.</span><span class="sxs-lookup"><span data-stu-id="54bf8-126">To force *early binding* (at compile time) and better performance, declare the variable with a specific class name, or cast it to the specific data type.</span></span>

  <span data-ttu-id="54bf8-127">Pokud deklarujete proměnnou objektu, zkuste použít konkrétní typ třídy, například <xref:System.OperatingSystem> namísto zobecněného `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="54bf8-127">When you declare an object variable, try to use a specific class type, for example <xref:System.OperatingSystem>, instead of the generalized `Object` type.</span></span> <span data-ttu-id="54bf8-128">Měli byste také použít nejvíce dostupné třídy, jako je například <xref:System.Windows.Forms.TextBox> namísto <xref:System.Windows.Forms.Control> , abyste měli přístup k jeho vlastnostem a metodám.</span><span class="sxs-lookup"><span data-stu-id="54bf8-128">You should also use the most specific class available, such as <xref:System.Windows.Forms.TextBox> instead of <xref:System.Windows.Forms.Control>, so that you can access its properties and methods.</span></span> <span data-ttu-id="54bf8-129">Můžete obvykle použít seznam **třídy** v **Prohlížeč objektů** k vyhledání dostupných názvů tříd.</span><span class="sxs-lookup"><span data-stu-id="54bf8-129">You can usually use the **Classes** list in the **Object Browser** to find available class names.</span></span>

- <span data-ttu-id="54bf8-130">**Rozšiřující.**</span><span class="sxs-lookup"><span data-stu-id="54bf8-130">**Widening.**</span></span> <span data-ttu-id="54bf8-131">Všechny datové typy a všechny typy odkazů se rozšíří na `Object` datový typ.</span><span class="sxs-lookup"><span data-stu-id="54bf8-131">All data types and all reference types widen to the `Object` data type.</span></span> <span data-ttu-id="54bf8-132">To znamená, že můžete převést libovolný typ na `Object` bez výskytu <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="54bf8-132">This means you can convert any type to `Object` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

  <span data-ttu-id="54bf8-133">Nicméně pokud převedete mezi typy hodnot a `Object` , Visual Basic provádí operace s názvem *zabalení* a *rozbalení*, které provádějí zpracování pomaleji.</span><span class="sxs-lookup"><span data-stu-id="54bf8-133">However, if you convert between value types and `Object`, Visual Basic performs operations called *boxing* and *unboxing*, which make execution slower.</span></span>

- <span data-ttu-id="54bf8-134">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="54bf8-134">**Type Characters.**</span></span> <span data-ttu-id="54bf8-135">`Object`nemá žádný znak typu literálu nebo znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="54bf8-135">`Object` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="54bf8-136">**Typ rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="54bf8-136">**Framework Type.**</span></span> <span data-ttu-id="54bf8-137">Odpovídající typ v .NET Framework je <xref:System.Object?displayProperty=nameWithType> Třída.</span><span class="sxs-lookup"><span data-stu-id="54bf8-137">The corresponding type in the .NET Framework is the <xref:System.Object?displayProperty=nameWithType> class.</span></span>

## <a name="example"></a><span data-ttu-id="54bf8-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="54bf8-138">Example</span></span>

<span data-ttu-id="54bf8-139">Následující příklad ukazuje `Object` proměnnou odkazující na instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="54bf8-139">The following example illustrates an `Object` variable pointing to an object instance.</span></span>

```vb
Dim objDb As Object
Dim myCollection As New Collection()
' Suppose myCollection has now been populated.
objDb = myCollection.Item(1)
```

## <a name="see-also"></a><span data-ttu-id="54bf8-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="54bf8-140">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="54bf8-141">Datové typy</span><span class="sxs-lookup"><span data-stu-id="54bf8-141">Data Types</span></span>](index.md)
- [<span data-ttu-id="54bf8-142">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="54bf8-142">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="54bf8-143">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="54bf8-143">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="54bf8-144">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="54bf8-144">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="54bf8-145">Postupy: Určení, zda dva objekty souvisejí.</span><span class="sxs-lookup"><span data-stu-id="54bf8-145">How to: Determine Whether Two Objects Are Related</span></span>](../../programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="54bf8-146">Postupy: Určení, zda dva objekty jsou identické</span><span class="sxs-lookup"><span data-stu-id="54bf8-146">How to: Determine Whether Two Objects Are Identical</span></span>](../../programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
