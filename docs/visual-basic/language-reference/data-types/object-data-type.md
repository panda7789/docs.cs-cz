---
title: "Datový typ objektu"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 847f2b50296ad1a1ba6f0009d1d6afced27f9abe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="object-data-type"></a><span data-ttu-id="4b189-102">Datový typ objektu</span><span class="sxs-lookup"><span data-stu-id="4b189-102">Object Data Type</span></span>
<span data-ttu-id="4b189-103">Obsahuje adresy, které odkazují na objekty.</span><span class="sxs-lookup"><span data-stu-id="4b189-103">Holds addresses that refer to objects.</span></span> <span data-ttu-id="4b189-104">Všechny odkaz (řetězec, pole, třídu nebo rozhraní) můžete přiřadit `Object` proměnné.</span><span class="sxs-lookup"><span data-stu-id="4b189-104">You can assign any reference type (string, array, class, or interface) to an `Object` variable.</span></span> <span data-ttu-id="4b189-105">`Object` Proměnné najdete také dat jakéhokoli typu hodnoty (numerickou `Boolean`, `Char`, `Date`, struktury nebo výčtové).</span><span class="sxs-lookup"><span data-stu-id="4b189-105">An `Object` variable can also refer to data of any value type (numeric, `Boolean`, `Char`, `Date`, structure, or enumeration).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b189-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b189-106">Remarks</span></span>  
 <span data-ttu-id="4b189-107">`Object` Datový typ může ukazovat na data jakéhokoli datového typu, včetně všechny instance objektu rozpozná vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="4b189-107">The `Object` data type can point to data of any data type, including any object instance your application recognizes.</span></span> <span data-ttu-id="4b189-108">Použití `Object` jaké datový typ proměnné může ukazovat Pokud si nejste jisti v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="4b189-108">Use `Object` when you do not know at compile time what data type the variable might point to.</span></span>  
  
 <span data-ttu-id="4b189-109">Výchozí hodnota `Object` je `Nothing` (odkaz s hodnotou null).</span><span class="sxs-lookup"><span data-stu-id="4b189-109">The default value of `Object` is `Nothing` (a null reference).</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="4b189-110">Datové typy</span><span class="sxs-lookup"><span data-stu-id="4b189-110">Data Types</span></span>  
 <span data-ttu-id="4b189-111">Můžete přiřadit proměnné, konstanta nebo výraz jakýkoli datový typ pro `Object` proměnné.</span><span class="sxs-lookup"><span data-stu-id="4b189-111">You can assign a variable, constant, or expression of any data type to an `Object` variable.</span></span> <span data-ttu-id="4b189-112">Určit typ dat `Object` proměnná aktuálně odkazuje, můžete použít <xref:System.Type.GetTypeCode%2A> metodu <xref:System.Type?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="4b189-112">To determine the data type an `Object` variable currently refers to, you can use the <xref:System.Type.GetTypeCode%2A> method of the <xref:System.Type?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="4b189-113">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="4b189-113">The following example illustrates this.</span></span>  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 <span data-ttu-id="4b189-114">`Object` Datový typ je typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="4b189-114">The `Object` data type is a reference type.</span></span> <span data-ttu-id="4b189-115">Však zpracovává jazyka Visual Basic `Object` jako typ hodnoty odkazuje na datový typ hodnoty proměnné.</span><span class="sxs-lookup"><span data-stu-id="4b189-115">However, Visual Basic treats an `Object` variable as a value type when it refers to data of a value type.</span></span>  
  
## <a name="storage"></a><span data-ttu-id="4b189-116">Úložiště</span><span class="sxs-lookup"><span data-stu-id="4b189-116">Storage</span></span>  
 <span data-ttu-id="4b189-117">Ať datový typ, který odkazuje na, `Object` proměnná neobsahuje hodnotu dat sám sebe, ale spíš ukazatel na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4b189-117">Whatever data type it refers to, an `Object` variable does not contain the data value itself, but rather a pointer to the value.</span></span> <span data-ttu-id="4b189-118">Vždy používá čtyři bajtů v paměti počítače, ale nezahrnuje úložiště pro data představující hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="4b189-118">It always uses four bytes in computer memory, but this does not include the storage for the data representing the value of the variable.</span></span> <span data-ttu-id="4b189-119">Z důvodu kód, který používá ukazatele vyhledejte data `Object` proměnné, která uchovává typů hodnot se nepatrně pomalejší přístup než explicitně typové proměnné.</span><span class="sxs-lookup"><span data-stu-id="4b189-119">Because of the code that uses the pointer to locate the data, `Object` variables holding value types are slightly slower to access than explicitly typed variables.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="4b189-120">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="4b189-120">Programming Tips</span></span>  
  
-   <span data-ttu-id="4b189-121">**Spolupráce aspekty.**</span><span class="sxs-lookup"><span data-stu-id="4b189-121">**Interop Considerations.**</span></span> <span data-ttu-id="4b189-122">Pokud jsou během propojení s součásti, které nejsou určeny pro rozhraní .NET Framework pro příklad objekty automatizace nebo COM, mějte na paměti, že typy ukazatelů v jiných prostředích nejsou kompatibilní s jazykem Visual Basic `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="4b189-122">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that pointer types in other environments are not compatible with the Visual Basic `Object` type.</span></span>  
  
-   <span data-ttu-id="4b189-123">**Výkon.**</span><span class="sxs-lookup"><span data-stu-id="4b189-123">**Performance.**</span></span> <span data-ttu-id="4b189-124">Proměnné deklarovat s `Object` typ je dostatečně flexibilní, aby obsahovat odkaz na libovolného objektu.</span><span class="sxs-lookup"><span data-stu-id="4b189-124">A variable you declare with the `Object` type is flexible enough to contain a reference to any object.</span></span> <span data-ttu-id="4b189-125">Ale při vyvolání metody nebo vlastnosti na tuto proměnnou, vždy platit *pozdní vazby* (za běhu).</span><span class="sxs-lookup"><span data-stu-id="4b189-125">However, when you invoke a method or property on such a variable, you always incur *late binding* (at run time).</span></span> <span data-ttu-id="4b189-126">Chcete-li vynutit *časné vazby* (v době kompilace) a vyšší výkon, deklarovat proměnnou s názvem určité třídy nebo přetypovat na typ konkrétní data.</span><span class="sxs-lookup"><span data-stu-id="4b189-126">To force *early binding* (at compile time) and better performance, declare the variable with a specific class name, or cast it to the specific data type.</span></span>  
  
     <span data-ttu-id="4b189-127">Po deklarování proměnné objektu zkuste použít konkrétní – třída typu, například <xref:System.OperatingSystem>, místo zobecněný `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="4b189-127">When you declare an object variable, try to use a specific class type, for example <xref:System.OperatingSystem>, instead of the generalized `Object` type.</span></span> <span data-ttu-id="4b189-128">Většina určité třídy, které jsou k dispozici, jako byste měli použít také <xref:System.Windows.Forms.TextBox> místo <xref:System.Windows.Forms.Control>tak, aby jeho vlastnosti a metody k dispozici.</span><span class="sxs-lookup"><span data-stu-id="4b189-128">You should also use the most specific class available, such as <xref:System.Windows.Forms.TextBox> instead of <xref:System.Windows.Forms.Control>, so that you can access its properties and methods.</span></span> <span data-ttu-id="4b189-129">Obvykle můžete používat **třídy** v seznamu **Prohlížeč objektů** najít názvy dostupných tříd.</span><span class="sxs-lookup"><span data-stu-id="4b189-129">You can usually use the **Classes** list in the **Object Browser** to find available class names.</span></span>  
  
-   <span data-ttu-id="4b189-130">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="4b189-130">**Widening.**</span></span> <span data-ttu-id="4b189-131">Všechny datové typy a všechny typy odkazu rozšíří do `Object` datového typu.</span><span class="sxs-lookup"><span data-stu-id="4b189-131">All data types and all reference types widen to the `Object` data type.</span></span> <span data-ttu-id="4b189-132">To znamená, že můžete převést do libovolného typu `Object` bez zjištění <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="4b189-132">This means you can convert any type to `Object` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
     <span data-ttu-id="4b189-133">Ale pokud převod mezi typy hodnot a `Object`, jazyka Visual Basic provádí operace názvem *zabalení* a *rozbalení*, ujistěte se, které provádění pomalejší.</span><span class="sxs-lookup"><span data-stu-id="4b189-133">However, if you convert between value types and `Object`, Visual Basic performs operations called *boxing* and *unboxing*, which make execution slower.</span></span>  
  
-   <span data-ttu-id="4b189-134">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="4b189-134">**Type Characters.**</span></span> <span data-ttu-id="4b189-135">`Object`nemá žádnou – znak typu literálu nebo – znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="4b189-135">`Object` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="4b189-136">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="4b189-136">**Framework Type.**</span></span> <span data-ttu-id="4b189-137">Typ odpovídající v rozhraní .NET Framework je <xref:System.Object?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="4b189-137">The corresponding type in the .NET Framework is the <xref:System.Object?displayProperty=nameWithType> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b189-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b189-138">Example</span></span>  
 <span data-ttu-id="4b189-139">Následující příklad ilustruje `Object` proměnné odkazující na instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="4b189-139">The following example illustrates an `Object` variable pointing to an object instance.</span></span>  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b189-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b189-140">See Also</span></span>  
 <xref:System.Object>  
 [<span data-ttu-id="4b189-141">Datové typy</span><span class="sxs-lookup"><span data-stu-id="4b189-141">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="4b189-142">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="4b189-142">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="4b189-143">Souhrn konverze</span><span class="sxs-lookup"><span data-stu-id="4b189-143">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="4b189-144">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="4b189-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="4b189-145">Postupy: určení, zda dva objekty souvisejí</span><span class="sxs-lookup"><span data-stu-id="4b189-145">How to: Determine Whether Two Objects Are Related</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [<span data-ttu-id="4b189-146">Postupy: určení, zda dva objekty jsou identické</span><span class="sxs-lookup"><span data-stu-id="4b189-146">How to: Determine Whether Two Objects Are Identical</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
