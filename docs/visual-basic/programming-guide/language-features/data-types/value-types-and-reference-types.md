---
title: Typy hodnot a typy odkazu
ms.date: 07/20/2015
helpviewer_keywords:
- reference data types [Visual Basic]
- reference types [Visual Basic]
- value types [Visual Basic]
- value data types [Visual Basic]
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
ms.openlocfilehash: f25caec43b7118b7b64db1b14516b0c5ea80f4f6
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504875"
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="b317d-102">Typy hodnot a typy odkazu</span><span class="sxs-lookup"><span data-stu-id="b317d-102">Value Types and Reference Types</span></span>
<span data-ttu-id="b317d-103">Existují dva druhy typů v jazyce Visual Basic: typy odkazu a typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="b317d-103">There are two kinds of types in Visual Basic: reference types and value types.</span></span> <span data-ttu-id="b317d-104">Proměnné typů odkazu ukládají odkazy na data (objekty), zatímco proměnné typů hodnoty data přímo obsahují příslušná data.</span><span class="sxs-lookup"><span data-stu-id="b317d-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="b317d-105">V případě typů odkazu mohou dvě proměnné odkazovat na stejný objekt. Operace v rámci jedné proměnné tedy mohou ovlivňovat objekt odkazovaný jinou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="b317d-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="b317d-106">S typy hodnot, každá proměnná má svou vlastní kopii dat, a není možné pro operace v rámci jedné proměnné k ovlivnit další (s výjimkou v případě třídy [ByRef modifikátor parametrů](../../../language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="b317d-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of the [ByRef modifier on parameters](../../../language-reference/modifiers/byref.md)).</span></span>
  
## <a name="value-types"></a><span data-ttu-id="b317d-107">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="b317d-107">Value Types</span></span>  
 <span data-ttu-id="b317d-108">Datový typ je *typ hodnoty* pokud obsahuje data v rámci své vlastní přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="b317d-108">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="b317d-109">Typy hodnot patří:</span><span class="sxs-lookup"><span data-stu-id="b317d-109">Value types include the following:</span></span>  
  
- <span data-ttu-id="b317d-110">Všechny číselné datové typy</span><span class="sxs-lookup"><span data-stu-id="b317d-110">All numeric data types</span></span>  
  
- <span data-ttu-id="b317d-111">`Boolean`, `Char`, a `Date`</span><span class="sxs-lookup"><span data-stu-id="b317d-111">`Boolean`, `Char`, and `Date`</span></span>  
  
- <span data-ttu-id="b317d-112">Všechny struktury, i když jejich členové jsou odkazové typy</span><span class="sxs-lookup"><span data-stu-id="b317d-112">All structures, even if their members are reference types</span></span>  
  
- <span data-ttu-id="b317d-113">Výčty, protože jeho základní typ je vždy `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, nebo `ULong`</span><span class="sxs-lookup"><span data-stu-id="b317d-113">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="b317d-114">Každý struktura je typ hodnoty, i v případě, že obsahuje členy typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="b317d-114">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="b317d-115">Z tohoto důvodu hodnotové typy, jako `Char` a `Integer` implementují struktury rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b317d-115">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="b317d-116">Typ hodnoty je možné deklarovat pomocí vyhrazené slovo, například `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="b317d-116">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="b317d-117">Můžete také použít `New` – klíčové slovo k inicializaci typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b317d-117">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="b317d-118">To je obzvláště užitečné, pokud typ má konstruktor, který používá parametry.</span><span class="sxs-lookup"><span data-stu-id="b317d-118">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="b317d-119">Příkladem je <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> konstruktor, který vytvoří nový `Decimal` hodnotu ze zadaného částí.</span><span class="sxs-lookup"><span data-stu-id="b317d-119">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="b317d-120">Typy odkazů</span><span class="sxs-lookup"><span data-stu-id="b317d-120">Reference Types</span></span>  
 <span data-ttu-id="b317d-121">A *odkazovat na typ* uchovává odkaz na svoje data.</span><span class="sxs-lookup"><span data-stu-id="b317d-121">A *reference type* stores a reference to its data.</span></span> <span data-ttu-id="b317d-122">Odkazové typy zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="b317d-122">Reference types include the following:</span></span>  
  
- `String`  
  
- <span data-ttu-id="b317d-123">Všechna pole, i když jsou jejich prvky typy hodnot</span><span class="sxs-lookup"><span data-stu-id="b317d-123">All arrays, even if their elements are value types</span></span>  
  
- <span data-ttu-id="b317d-124">Typy, jako například tříd <xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="b317d-124">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
- <span data-ttu-id="b317d-125">Delegáty</span><span class="sxs-lookup"><span data-stu-id="b317d-125">Delegates</span></span>  
  
 <span data-ttu-id="b317d-126">Třída je *odkazovat na typ*.</span><span class="sxs-lookup"><span data-stu-id="b317d-126">A class is a *reference type*.</span></span> <span data-ttu-id="b317d-127">Upozorňujeme, že každé pole typu odkazu, i v případě, že její členy jsou typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="b317d-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="b317d-128">Protože každý odkaz na typ představuje základní třídy rozhraní .NET Framework, je nutné použít [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md) – klíčové slovo je inicializovat.</span><span class="sxs-lookup"><span data-stu-id="b317d-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="b317d-129">Následující příkaz inicializuje pole.</span><span class="sxs-lookup"><span data-stu-id="b317d-129">The following statement initializes an array.</span></span>  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="b317d-130">Prvky, které nejsou typy</span><span class="sxs-lookup"><span data-stu-id="b317d-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="b317d-131">Následující programovací prvky nekvalifikujte jako typy, protože některý z nich nelze zadat pro element deklarovaný typ dat:</span><span class="sxs-lookup"><span data-stu-id="b317d-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
- <span data-ttu-id="b317d-132">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="b317d-132">Namespaces</span></span>  
  
- <span data-ttu-id="b317d-133">Moduly</span><span class="sxs-lookup"><span data-stu-id="b317d-133">Modules</span></span>  
  
- <span data-ttu-id="b317d-134">Události</span><span class="sxs-lookup"><span data-stu-id="b317d-134">Events</span></span>  
  
- <span data-ttu-id="b317d-135">Vlastnosti a postupy</span><span class="sxs-lookup"><span data-stu-id="b317d-135">Properties and procedures</span></span>  
  
- <span data-ttu-id="b317d-136">Proměnné, konstanty a pole</span><span class="sxs-lookup"><span data-stu-id="b317d-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="b317d-137">Práce s datovým typem objektu</span><span class="sxs-lookup"><span data-stu-id="b317d-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="b317d-138">Proměnné můžete přiřadit odkazový typ nebo hodnotový typ `Object` datového typu.</span><span class="sxs-lookup"><span data-stu-id="b317d-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="b317d-139">`Object` Proměnná vždy obsahuje odkaz na data, nikdy vlastní data.</span><span class="sxs-lookup"><span data-stu-id="b317d-139">An `Object` variable always holds a reference to the data, never the data itself.</span></span> <span data-ttu-id="b317d-140">Nicméně pokud přiřadíte typ hodnoty do `Object` proměnné, se chová jako obsahuje vlastní data.</span><span class="sxs-lookup"><span data-stu-id="b317d-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="b317d-141">Další informace najdete v tématu [datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="b317d-141">For more information, see [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="b317d-142">Můžete zjistit, jestli se `Object` proměnné funguje jako odkaz na typ nebo hodnotový typ ji do <xref:Microsoft.VisualBasic.Information.IsReference%2A> metoda ve <xref:Microsoft.VisualBasic.Information> třídu <xref:Microsoft.VisualBasic?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b317d-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="b317d-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> Vrátí `True` Pokud obsah `Object` proměnná představuje typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="b317d-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b317d-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b317d-144">See also</span></span>

- [<span data-ttu-id="b317d-145">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="b317d-145">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="b317d-146">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b317d-146">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="b317d-147">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="b317d-147">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="b317d-148">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="b317d-148">Efficient Use of Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="b317d-149">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="b317d-149">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="b317d-150">Datové typy</span><span class="sxs-lookup"><span data-stu-id="b317d-150">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
