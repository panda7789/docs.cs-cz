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
ms.openlocfilehash: 616110145db2796e05509094b1c023daacd68f03
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835567"
---
# <a name="object-data-type"></a><span data-ttu-id="99cce-102">Datový typ objektu</span><span class="sxs-lookup"><span data-stu-id="99cce-102">Object Data Type</span></span>
<span data-ttu-id="99cce-103">Obsahuje adresy, které odkazují na objekty.</span><span class="sxs-lookup"><span data-stu-id="99cce-103">Holds addresses that refer to objects.</span></span> <span data-ttu-id="99cce-104">Jakýkoli odkaz na typ (řetězec, pole, třídy nebo rozhraní) můžete přiřadit `Object` proměnné.</span><span class="sxs-lookup"><span data-stu-id="99cce-104">You can assign any reference type (string, array, class, or interface) to an `Object` variable.</span></span> <span data-ttu-id="99cce-105">`Object` Proměnné lze také odkazovat na data libovolného typu hodnoty (číselné, `Boolean`, `Char`, `Date`, struktury nebo výčet).</span><span class="sxs-lookup"><span data-stu-id="99cce-105">An `Object` variable can also refer to data of any value type (numeric, `Boolean`, `Char`, `Date`, structure, or enumeration).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99cce-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="99cce-106">Remarks</span></span>  
 <span data-ttu-id="99cce-107">`Object` Datový typ může odkazovat na data z libovolného datového typu, včetně všechny instance objektu rozpozná vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="99cce-107">The `Object` data type can point to data of any data type, including any object instance your application recognizes.</span></span> <span data-ttu-id="99cce-108">Použití `Object` Pokud si nejste jisti v době kompilace, jaký datový typ proměnné může ukazovat na.</span><span class="sxs-lookup"><span data-stu-id="99cce-108">Use `Object` when you do not know at compile time what data type the variable might point to.</span></span>  
  
 <span data-ttu-id="99cce-109">Výchozí hodnota `Object` je `Nothing` (odkaz s hodnotou null).</span><span class="sxs-lookup"><span data-stu-id="99cce-109">The default value of `Object` is `Nothing` (a null reference).</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="99cce-110">Datové typy</span><span class="sxs-lookup"><span data-stu-id="99cce-110">Data Types</span></span>  
 <span data-ttu-id="99cce-111">Můžete přiřadit proměnné, konstanty nebo výrazu libovolného datového typu pro `Object` proměnné.</span><span class="sxs-lookup"><span data-stu-id="99cce-111">You can assign a variable, constant, or expression of any data type to an `Object` variable.</span></span> <span data-ttu-id="99cce-112">Určit typ dat `Object` proměnná aktuálně odkazuje, můžete použít <xref:System.Type.GetTypeCode%2A> metodu <xref:System.Type?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="99cce-112">To determine the data type an `Object` variable currently refers to, you can use the <xref:System.Type.GetTypeCode%2A> method of the <xref:System.Type?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="99cce-113">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="99cce-113">The following example illustrates this.</span></span>  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 <span data-ttu-id="99cce-114">`Object` Datový typ je typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="99cce-114">The `Object` data type is a reference type.</span></span> <span data-ttu-id="99cce-115">Však zpracovává jazyka Visual Basic `Object` proměnné jako typ hodnoty, když se odkazuje na datový typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="99cce-115">However, Visual Basic treats an `Object` variable as a value type when it refers to data of a value type.</span></span>  
  
## <a name="storage"></a><span data-ttu-id="99cce-116">Úložiště</span><span class="sxs-lookup"><span data-stu-id="99cce-116">Storage</span></span>  
 <span data-ttu-id="99cce-117">Jakýkoli datový typ, na který odkazuje, `Object` proměnné samotné, ale spíše ukazatel na hodnotu neobsahuje hodnotu data.</span><span class="sxs-lookup"><span data-stu-id="99cce-117">Whatever data type it refers to, an `Object` variable does not contain the data value itself, but rather a pointer to the value.</span></span> <span data-ttu-id="99cce-118">Vždy používá čtyři bajty v paměti počítače, ale nezahrnuje úložiště pro data představující hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="99cce-118">It always uses four bytes in computer memory, but this does not include the storage for the data representing the value of the variable.</span></span> <span data-ttu-id="99cce-119">Z důvodu kód, který používá ukazatel vyhledejte data `Object` proměnné obsahující typy hodnot jsou o něco pomalejší než explicitně přístup k zadané proměnné.</span><span class="sxs-lookup"><span data-stu-id="99cce-119">Because of the code that uses the pointer to locate the data, `Object` variables holding value types are slightly slower to access than explicitly typed variables.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="99cce-120">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="99cce-120">Programming Tips</span></span>  
  
-   <span data-ttu-id="99cce-121">**Spolupráce aspekty.**</span><span class="sxs-lookup"><span data-stu-id="99cce-121">**Interop Considerations.**</span></span> <span data-ttu-id="99cce-122">Při vzájemném propojování součástí, které nejsou napsané pro rozhraní .NET Framework, například objekty automatizace nebo COM, mějte na paměti, že typy ukazatelů v jiných prostředích nejsou kompatibilní s jazykem Visual Basic `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="99cce-122">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that pointer types in other environments are not compatible with the Visual Basic `Object` type.</span></span>  
  
-   <span data-ttu-id="99cce-123">**Výkon.**</span><span class="sxs-lookup"><span data-stu-id="99cce-123">**Performance.**</span></span> <span data-ttu-id="99cce-124">Proměnná deklarovaná pomocí `Object` typ je dostatečně flexibilní, aby obsahují odkaz na libovolný objekt.</span><span class="sxs-lookup"><span data-stu-id="99cce-124">A variable you declare with the `Object` type is flexible enough to contain a reference to any object.</span></span> <span data-ttu-id="99cce-125">Nicméně při vyvolání metody nebo vlastnosti na tyto proměnné se vždy vynakládají *pozdní vazby* (za běhu).</span><span class="sxs-lookup"><span data-stu-id="99cce-125">However, when you invoke a method or property on such a variable, you always incur *late binding* (at run time).</span></span> <span data-ttu-id="99cce-126">Chcete-li vynutit *časné vazby* (v době kompilace) a lepšího výkonu, deklarujte proměnnou s názvem určité třídy nebo přetypován na určitý datový typ.</span><span class="sxs-lookup"><span data-stu-id="99cce-126">To force *early binding* (at compile time) and better performance, declare the variable with a specific class name, or cast it to the specific data type.</span></span>  
  
     <span data-ttu-id="99cce-127">Při deklaraci proměnné objektu, zkuste použít určitý typ třídy, například <xref:System.OperatingSystem>, místo zobecněný `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="99cce-127">When you declare an object variable, try to use a specific class type, for example <xref:System.OperatingSystem>, instead of the generalized `Object` type.</span></span> <span data-ttu-id="99cce-128">By měl také použít k dispozici, například na třídu nejspecifičtější <xref:System.Windows.Forms.TextBox> místo <xref:System.Windows.Forms.Control>, aby přístup k jeho vlastnosti a metody.</span><span class="sxs-lookup"><span data-stu-id="99cce-128">You should also use the most specific class available, such as <xref:System.Windows.Forms.TextBox> instead of <xref:System.Windows.Forms.Control>, so that you can access its properties and methods.</span></span> <span data-ttu-id="99cce-129">Můžete obvykle použít **třídy** v seznamu **prohlížeče objektů** najít názvy tříd k dispozici.</span><span class="sxs-lookup"><span data-stu-id="99cce-129">You can usually use the **Classes** list in the **Object Browser** to find available class names.</span></span>  
  
-   <span data-ttu-id="99cce-130">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="99cce-130">**Widening.**</span></span> <span data-ttu-id="99cce-131">Všechny typy dat a všechny typy odkazů rozšířit na `Object` datového typu.</span><span class="sxs-lookup"><span data-stu-id="99cce-131">All data types and all reference types widen to the `Object` data type.</span></span> <span data-ttu-id="99cce-132">To znamená, že lze převést libovolný typ `Object` aniž se objeví <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="99cce-132">This means you can convert any type to `Object` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
     <span data-ttu-id="99cce-133">Ale při převodu mezi typy hodnot a `Object`, Visual Basic provádí operace volat *zabalení* a *rozbalení*, ujistěte se, které provádění pomalejší.</span><span class="sxs-lookup"><span data-stu-id="99cce-133">However, if you convert between value types and `Object`, Visual Basic performs operations called *boxing* and *unboxing*, which make execution slower.</span></span>  
  
-   <span data-ttu-id="99cce-134">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="99cce-134">**Type Characters.**</span></span> <span data-ttu-id="99cce-135">`Object` nemá žádný – znak typu literálu nebo – znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="99cce-135">`Object` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="99cce-136">**Typ architektury.**</span><span class="sxs-lookup"><span data-stu-id="99cce-136">**Framework Type.**</span></span> <span data-ttu-id="99cce-137">Odpovídajícím typem v rozhraní .NET Framework je <xref:System.Object?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="99cce-137">The corresponding type in the .NET Framework is the <xref:System.Object?displayProperty=nameWithType> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99cce-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="99cce-138">Example</span></span>  
 <span data-ttu-id="99cce-139">Následující příklad ukazuje `Object` proměnná odkazuje na instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="99cce-139">The following example illustrates an `Object` variable pointing to an object instance.</span></span>  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## <a name="see-also"></a><span data-ttu-id="99cce-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99cce-140">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="99cce-141">Datové typy</span><span class="sxs-lookup"><span data-stu-id="99cce-141">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="99cce-142">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="99cce-142">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="99cce-143">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="99cce-143">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="99cce-144">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="99cce-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="99cce-145">Postupy: Určení, zda dva objekty souvisejí</span><span class="sxs-lookup"><span data-stu-id="99cce-145">How to: Determine Whether Two Objects Are Related</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="99cce-146">Postupy: Určení, zda dva objekty jsou identické</span><span class="sxs-lookup"><span data-stu-id="99cce-146">How to: Determine Whether Two Objects Are Identical</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
