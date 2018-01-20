---
title: "Přetypování a převody typů (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
caps.latest.revision: "52"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1361a7f115e2bae4b2d1f6271fa9020706581691
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="casting-and-type-conversions-c-programming-guide"></a><span data-ttu-id="545d5-102">Přetypování a převody typů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="545d5-102">Casting and Type Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="545d5-103">Protože C# je staticky zadali v době kompilace po proměnné je deklarovaná, nemůže být znovu deklarován nebo používat k ukládání hodnoty jiného typu, pokud je tento typ převést na typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="545d5-103">Because C# is statically-typed at compile time, after a variable is declared, it cannot be declared again or used to store values of another type unless that type is convertible to the variable's type.</span></span> <span data-ttu-id="545d5-104">Není třeba žádný převod z celé číslo na libovolný libovolný řetězec.</span><span class="sxs-lookup"><span data-stu-id="545d5-104">For example, there is no conversion from an integer to any arbitrary string.</span></span> <span data-ttu-id="545d5-105">Proto po deklarovat `i` jako celé číslo, nelze přiřadit řetězec "Hello", jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="545d5-105">Therefore, after you declare `i` as an integer, you cannot assign the string "Hello" to it, as is shown in the following code.</span></span>  
  
```csharp  
int i;  
i = "Hello"; // Error: "Cannot implicitly convert type 'string' to 'int'"  
```  
  
 <span data-ttu-id="545d5-106">Však může někdy musíte zkopírovat hodnotu do proměnné nebo metoda parametru jiného typu.</span><span class="sxs-lookup"><span data-stu-id="545d5-106">However, you might sometimes need to copy a value into a variable or method parameter of another type.</span></span> <span data-ttu-id="545d5-107">Například můžete mít proměnná typu integer, které potřebujete předat do metody, jejichž parametr je zadán jako `double`.</span><span class="sxs-lookup"><span data-stu-id="545d5-107">For example, you might have an integer variable that you need to pass to a method whose parameter is typed as `double`.</span></span> <span data-ttu-id="545d5-108">Nebo možná budete muset přiřadit proměnné třídy proměnné typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="545d5-108">Or you might need to assign a class variable to a variable of an interface type.</span></span> <span data-ttu-id="545d5-109">Tyto typy operací se nazývají *převody typu*.</span><span class="sxs-lookup"><span data-stu-id="545d5-109">These kinds of operations are called *type conversions*.</span></span> <span data-ttu-id="545d5-110">V jazyce C# můžete provést následující typy převody:</span><span class="sxs-lookup"><span data-stu-id="545d5-110">In C#, you can perform the following kinds of conversions:</span></span>  
  
-   <span data-ttu-id="545d5-111">**Implicitní převody**: žádné speciální syntaxe není nutná převod je typově bezpečný a žádná data se ztratí.</span><span class="sxs-lookup"><span data-stu-id="545d5-111">**Implicit conversions**: No special syntax is required because the conversion is type safe and no data will be lost.</span></span> <span data-ttu-id="545d5-112">Mezi příklady patří převody z menší na větší integrální typy a převody z odvozené třídy základní třídy.</span><span class="sxs-lookup"><span data-stu-id="545d5-112">Examples include conversions from smaller to larger integral types, and conversions from derived classes to base classes.</span></span>  
  
-   <span data-ttu-id="545d5-113">**Explicitní převody (přetypování)**: explicitní převody vyžadují operátor přetypování.</span><span class="sxs-lookup"><span data-stu-id="545d5-113">**Explicit conversions (casts)**: Explicit conversions require a cast operator.</span></span> <span data-ttu-id="545d5-114">Když při převodu dojít ke ztrátě informací, nebo při převodu se nemusí zdařit z jiných důvodů je potřeba přetypování.</span><span class="sxs-lookup"><span data-stu-id="545d5-114">Casting is required when information might be lost in the conversion, or when the conversion might not succeed for other reasons.</span></span>  <span data-ttu-id="545d5-115">Typické příklady zahrnují číselný převod na typ, který má menší přesnost nebo určený menším rozsahem a převod instance základní třídy odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="545d5-115">Typical examples include numeric conversion to a type that has less precision or a smaller range, and conversion of a base-class instance to a derived class.</span></span>  
  
-   <span data-ttu-id="545d5-116">**Uživatelem definované převody**: uživatelem definované převody provádí speciální metody, které můžete definovat povolit explicitní a implicitní převody mezi vlastní typy, které nemají relaci základní třída – odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="545d5-116">**User-defined conversions**: User-defined conversions are performed by special methods that you can define to enable explicit and implicit conversions between custom types that do not have a base class–derived class relationship.</span></span> <span data-ttu-id="545d5-117">Další informace najdete v tématu [operátory převodu](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="545d5-117">For more information, see [Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md).</span></span>  
  
-   <span data-ttu-id="545d5-118">**Převody s pomocné třídy**: pro převod mezi nekompatibilní typy, jako je celá čísla a <xref:System.DateTime?displayProperty=nameWithType> objekty, nebo hexadecimální řetězce a pole bajtů, můžete použít <xref:System.BitConverter?displayProperty=nameWithType> třídy, <xref:System.Convert?displayProperty=nameWithType> třídy a `Parse`metody předdefinované číselné typy, jako například <xref:System.Int32.Parse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="545d5-118">**Conversions with helper classes**: To convert between non-compatible types, such as integers and <xref:System.DateTime?displayProperty=nameWithType> objects, or hexadecimal strings and byte arrays, you can use the <xref:System.BitConverter?displayProperty=nameWithType> class, the <xref:System.Convert?displayProperty=nameWithType> class, and the `Parse` methods of the built-in numeric types, such as <xref:System.Int32.Parse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="545d5-119">Další informace najdete v tématu [postupy: převedení pole bajtů na typ int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [postupy: převedení řetězce na číslo](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), a [postupy: převod mezi hexadecimálními řetězci a číselnými typy](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="545d5-119">For more information, see [How to: Convert a byte Array to an int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [How to: Convert a String to a Number](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), and [How to: Convert Between Hexadecimal Strings and Numeric Types](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).</span></span>  
  
## <a name="implicit-conversions"></a><span data-ttu-id="545d5-120">Implicitní převody</span><span class="sxs-lookup"><span data-stu-id="545d5-120">Implicit Conversions</span></span>  
 <span data-ttu-id="545d5-121">Pro předdefinované číselnými typy implicitní převod můžete provést, když hodnota, která má být uložen můžete začlenit do proměnné bez se zkrátí nebo zaokrouhlen.</span><span class="sxs-lookup"><span data-stu-id="545d5-121">For built-in numeric types, an implicit conversion can be made when the value to be stored can fit into the variable without being truncated or rounded off.</span></span> <span data-ttu-id="545d5-122">Například proměnná typu [dlouho](../../../csharp/language-reference/keywords/long.md) (celé číslo na 8 bajtů) může ukládat všechny hodnoty, které [int](../../../csharp/language-reference/keywords/int.md) můžete ukládat (4 bajty v počítači 32bitová verze).</span><span class="sxs-lookup"><span data-stu-id="545d5-122">For example, a variable of type [long](../../../csharp/language-reference/keywords/long.md) (8 byte integer) can store any value that an [int](../../../csharp/language-reference/keywords/int.md) (4 bytes on a 32-bit computer) can store.</span></span> <span data-ttu-id="545d5-123">V následujícím příkladu, kompilátor implicitně převede hodnotu na pravé straně typu `long` před přiřazením jeho `bigNum`.</span><span class="sxs-lookup"><span data-stu-id="545d5-123">In the following example, the compiler implicitly converts the value on the right to a type `long` before assigning it to `bigNum`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#34](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_1.cs)]  
  
 <span data-ttu-id="545d5-124">Úplný seznam všech implicitních číselných převodů, najdete v části [implicitní číselné převody tabulky](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="545d5-124">For a complete list of all implicit numeric conversions, see [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
 <span data-ttu-id="545d5-125">U typů odkazu existuje vždy implicitní převod z třídy na některý z jeho přímý nebo nepřímý základní třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="545d5-125">For reference types, an implicit conversion always exists from a class to any one of its direct or indirect base classes or interfaces.</span></span> <span data-ttu-id="545d5-126">Žádné speciální syntaxe je nutné, protože do odvozené třídy vždy obsahuje všechny členy základní třídy.</span><span class="sxs-lookup"><span data-stu-id="545d5-126">No special syntax is necessary because a derived class always contains all the members of a base class.</span></span>  
  
```  
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a><span data-ttu-id="545d5-127">Explicitní převody</span><span class="sxs-lookup"><span data-stu-id="545d5-127">Explicit Conversions</span></span>  
 <span data-ttu-id="545d5-128">Ale pokud převod nelze provést bez riziko ztráty informací, kompilátor vyžaduje provedení explicitní převod, která se nazývá *přetypování*.</span><span class="sxs-lookup"><span data-stu-id="545d5-128">However, if a conversion cannot be made without a risk of losing information, the compiler requires that you perform an explicit conversion, which is called a *cast*.</span></span> <span data-ttu-id="545d5-129">Přetypování představuje způsob, kterou chcete provést převod a že jste si vědomi, že může dojít ke ztrátě dat. explicitně informuje o kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="545d5-129">A cast is a way of explicitly informing the compiler that you intend to make the conversion and that you are aware that data loss might occur.</span></span> <span data-ttu-id="545d5-130">Pokud chcete provést přetypování, zadejte typ, který se přetypování na v závorkách před hodnota nebo proměnná, která má být převeden.</span><span class="sxs-lookup"><span data-stu-id="545d5-130">To perform a cast, specify the type that you are casting to in parentheses in front of the value or variable to be converted.</span></span> <span data-ttu-id="545d5-131">Tento program přetypování [dvojité](../../../csharp/language-reference/keywords/double.md) k [int](../../../csharp/language-reference/keywords/int.md). Program nebude kompilovat bez přetypování.</span><span class="sxs-lookup"><span data-stu-id="545d5-131">The following program casts a [double](../../../csharp/language-reference/keywords/double.md) to an [int](../../../csharp/language-reference/keywords/int.md). The program will not compile without the cast.</span></span>  
  
 [!code-csharp[csProgGuideTypes#2](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_2.cs)]  
  
 <span data-ttu-id="545d5-132">Seznam explicitních číselných převodů, které jsou povoleny, naleznete v části [explicitní číselné převody tabulky](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="545d5-132">For a list of the explicit numeric conversions that are allowed, see [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span></span>  
  
 <span data-ttu-id="545d5-133">U typů odkazu se vyžaduje explicitní přetypování, pokud je potřeba převést na odvozený typ základní typ:</span><span class="sxs-lookup"><span data-stu-id="545d5-133">For reference types, an explicit cast is required if you need to convert from a base type to a derived type:</span></span>  
  
```csharp  
// Create a new derived type.  
Giraffe g = new Giraffe();  
  
// Implicit conversion to base type is safe.  
Animal a = g;  
  
// Explicit conversion is required to cast back  
// to derived type. Note: This will compile but will  
// throw an exception at run time if the right-side  
// object is not in fact a Giraffe.  
Giraffe g2 = (Giraffe) a;  
```  
  
 <span data-ttu-id="545d5-134">Přetypování operace mezi odkazové typy nezmění běhového typu podkladového objektu; změní pouze typ hodnoty, který se používá jako odkaz na tento objekt.</span><span class="sxs-lookup"><span data-stu-id="545d5-134">A cast operation between reference types does not change the run-time type of the underlying object; it only changes the type of the value that is being used as a reference to that object.</span></span> <span data-ttu-id="545d5-135">Další informace najdete v tématu [polymorfismus](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).</span><span class="sxs-lookup"><span data-stu-id="545d5-135">For more information, see [Polymorphism](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).</span></span>  
  
## <a name="type-conversion-exceptions-at-run-time"></a><span data-ttu-id="545d5-136">Typ převodu výjimky za běhu</span><span class="sxs-lookup"><span data-stu-id="545d5-136">Type Conversion Exceptions at Run Time</span></span>  
 <span data-ttu-id="545d5-137">V některých převody typu odkaz nemůže kompilátor zjistit, zda přetypování budou platné.</span><span class="sxs-lookup"><span data-stu-id="545d5-137">In some reference type conversions, the compiler cannot determine whether a cast will be valid.</span></span> <span data-ttu-id="545d5-138">Je možné pro přetypování operaci, která správně zkompiluje selhání za běhu.</span><span class="sxs-lookup"><span data-stu-id="545d5-138">It is possible for a cast operation that compiles correctly to fail at run time.</span></span> <span data-ttu-id="545d5-139">Jak je znázorněno v následujícím příkladu, přetypovat typ, způsobí, že selže v době běhu <xref:System.InvalidCastException> vyvolání.</span><span class="sxs-lookup"><span data-stu-id="545d5-139">As shown in the following example, a type cast that fails at run time will cause an <xref:System.InvalidCastException> to be thrown.</span></span>  
  
 [!code-csharp[csProgGuideTypes#41](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_3.cs)]  
  
 <span data-ttu-id="545d5-140">C# poskytuje [je](../../../csharp/language-reference/keywords/is.md) a [jako](../../../csharp/language-reference/keywords/as.md) operátory umožnit pro testování kompatibility před provedením ve skutečnosti přetypování.</span><span class="sxs-lookup"><span data-stu-id="545d5-140">C# provides the [is](../../../csharp/language-reference/keywords/is.md) and [as](../../../csharp/language-reference/keywords/as.md) operators to enable you to test for compatibility before actually performing a cast.</span></span> <span data-ttu-id="545d5-141">Další informace najdete v tématu [postupy: bezpečné přetypování pomocí jako a je operátory](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md).</span><span class="sxs-lookup"><span data-stu-id="545d5-141">For more information, see [How to: Safely Cast by Using as and is Operators](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="545d5-142">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="545d5-142">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a><span data-ttu-id="545d5-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="545d5-143">See Also</span></span>  
 [<span data-ttu-id="545d5-144">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="545d5-144">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="545d5-145">Typy</span><span class="sxs-lookup"><span data-stu-id="545d5-145">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="545d5-146">() – operátor</span><span class="sxs-lookup"><span data-stu-id="545d5-146">() Operator</span></span>](../../../csharp/language-reference/operators/invocation-operator.md)  
 [<span data-ttu-id="545d5-147">explicit</span><span class="sxs-lookup"><span data-stu-id="545d5-147">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="545d5-148">implicit</span><span class="sxs-lookup"><span data-stu-id="545d5-148">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
 [<span data-ttu-id="545d5-149">Operátory převodu</span><span class="sxs-lookup"><span data-stu-id="545d5-149">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
 [<span data-ttu-id="545d5-150">Převod zobecněný typů</span><span class="sxs-lookup"><span data-stu-id="545d5-150">Generalized Type Conversion</span></span>](http://msdn.microsoft.com/library/49253ae6-7657-4810-82ab-1176a6feeada)  
 [<span data-ttu-id="545d5-151">Převod exportovaný typů</span><span class="sxs-lookup"><span data-stu-id="545d5-151">Exported Type Conversion</span></span>](http://msdn.microsoft.com/library/1dfe55f4-07a2-4b61-aabf-a8cf65783a6b)  
 [<span data-ttu-id="545d5-152">Postupy: Převedení řetězce na číslo</span><span class="sxs-lookup"><span data-stu-id="545d5-152">How to: Convert a String to a Number</span></span>](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)
