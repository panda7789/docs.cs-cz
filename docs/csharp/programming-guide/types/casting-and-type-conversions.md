---
title: Přetypování a převody typu – C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
ms.openlocfilehash: 80ff658774c776545eb7d5158b4abd451f7fcf7d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61709364"
---
# <a name="casting-and-type-conversions-c-programming-guide"></a><span data-ttu-id="8a986-102">Přetypování a převody typu (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="8a986-102">Casting and type conversions (C# Programming Guide)</span></span>

<span data-ttu-id="8a986-103">C# je staticky typovaný v době kompilace, jakmile je proměnná deklarována, nemůže být znovu deklarován nebo mu přiřazena hodnota jiného typu, pokud je tento typ implicitně převést na typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="8a986-103">Because C# is statically-typed at compile time, after a variable is declared, it cannot be declared again or assigned a value of another type unless that type is implicitly convertible to the variable's type.</span></span> <span data-ttu-id="8a986-104">Například `string` nejde implicitně převést na `int`.</span><span class="sxs-lookup"><span data-stu-id="8a986-104">For example, the `string` cannot be implicitly converted to `int`.</span></span> <span data-ttu-id="8a986-105">Proto po deklarování `i` jako `int`, nelze přiřadit řetězec "Hello", jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="8a986-105">Therefore, after you declare `i` as an `int`, you cannot assign the string "Hello" to it, as the following code shows:</span></span>
  
```csharp  
int i;  
i = "Hello"; // error CS0029: Cannot implicitly convert type 'string' to 'int'
```  
  
 <span data-ttu-id="8a986-106">Však můžete někdy potřebovat zkopírovat hodnotu do proměnné nebo metody parametr jiného typu.</span><span class="sxs-lookup"><span data-stu-id="8a986-106">However, you might sometimes need to copy a value into a variable or method parameter of another type.</span></span> <span data-ttu-id="8a986-107">Například můžete mít celočíselnou proměnnou, která je potřeba předat metodě, jehož parametr zadán jako `double`.</span><span class="sxs-lookup"><span data-stu-id="8a986-107">For example, you might have an integer variable that you need to pass to a method whose parameter is typed as `double`.</span></span> <span data-ttu-id="8a986-108">Nebo možná budete muset proměnné třídy přiřadit proměnné typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8a986-108">Or you might need to assign a class variable to a variable of an interface type.</span></span> <span data-ttu-id="8a986-109">Tyto typy operací jsou volány *převody typů*.</span><span class="sxs-lookup"><span data-stu-id="8a986-109">These kinds of operations are called *type conversions*.</span></span> <span data-ttu-id="8a986-110">V jazyce C# můžete provést následující druhy převody:</span><span class="sxs-lookup"><span data-stu-id="8a986-110">In C#, you can perform the following kinds of conversions:</span></span>  
  
- <span data-ttu-id="8a986-111">**Implicitní převody**: Žádná speciální syntax není nutná, protože převod je typově bezpečný a žádná data se ztratí.</span><span class="sxs-lookup"><span data-stu-id="8a986-111">**Implicit conversions**: No special syntax is required because the conversion is type safe and no data will be lost.</span></span> <span data-ttu-id="8a986-112">Mezi příklady patří převody z menších na větší celočíselné typy a převody z odvozené třídy základní třídy.</span><span class="sxs-lookup"><span data-stu-id="8a986-112">Examples include conversions from smaller to larger integral types, and conversions from derived classes to base classes.</span></span>  
  
- <span data-ttu-id="8a986-113">**Explicitní převody (přetypování)**: Explicitní převody vyžadují operátor přetypování.</span><span class="sxs-lookup"><span data-stu-id="8a986-113">**Explicit conversions (casts)**: Explicit conversions require a cast operator.</span></span> <span data-ttu-id="8a986-114">Přetypování je povinný při převodu dojít ke ztrátě informací nebo při převodu se nemusí zdařit z jiných důvodů.</span><span class="sxs-lookup"><span data-stu-id="8a986-114">Casting is required when information might be lost in the conversion, or when the conversion might not succeed for other reasons.</span></span>  <span data-ttu-id="8a986-115">Typické příklady zahrnují číselný převod na typ, který má nižší přesnost nebo menší rozsah a převodu instance základní třídy na odvozenou třídu.</span><span class="sxs-lookup"><span data-stu-id="8a986-115">Typical examples include numeric conversion to a type that has less precision or a smaller range, and conversion of a base-class instance to a derived class.</span></span>  
  
- <span data-ttu-id="8a986-116">**Uživatelem definované převody**: Uživatelem definované převody jsou prováděny speciální metody, které můžete definovat umožňuje explicitní a implicitní převody mezi vlastní typy, které nemají vztah základní třídy – odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="8a986-116">**User-defined conversions**: User-defined conversions are performed by special methods that you can define to enable explicit and implicit conversions between custom types that do not have a base class–derived class relationship.</span></span> <span data-ttu-id="8a986-117">Další informace najdete v tématu [operátory převodu](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="8a986-117">For more information, see [Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md).</span></span>  
  
- <span data-ttu-id="8a986-118">**Převod pomocí tříd pomocných rutin**: K převodu mezi nekompatibilními typy, jako jsou celá čísla a <xref:System.DateTime?displayProperty=nameWithType> objektů, nebo hexadecimálními řetězci a bajtová pole, můžete použít <xref:System.BitConverter?displayProperty=nameWithType> třídy, <xref:System.Convert?displayProperty=nameWithType> třídy a `Parse` metody předdefinované číselné typy, jako <xref:System.Int32.Parse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8a986-118">**Conversions with helper classes**: To convert between non-compatible types, such as integers and <xref:System.DateTime?displayProperty=nameWithType> objects, or hexadecimal strings and byte arrays, you can use the <xref:System.BitConverter?displayProperty=nameWithType> class, the <xref:System.Convert?displayProperty=nameWithType> class, and the `Parse` methods of the built-in numeric types, such as <xref:System.Int32.Parse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8a986-119">Další informace najdete v tématu [jak: Převedení pole bajtů na typ int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [jak: Převod řetězce na číslo](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), a [jak: Převod mezi hexadecimálními řetězci a číselnými typy](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="8a986-119">For more information, see [How to: Convert a byte Array to an int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [How to: Convert a String to a Number](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), and [How to: Convert Between Hexadecimal Strings and Numeric Types](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).</span></span>  
  
## <a name="implicit-conversions"></a><span data-ttu-id="8a986-120">Implicitní převody</span><span class="sxs-lookup"><span data-stu-id="8a986-120">Implicit conversions</span></span>

 <span data-ttu-id="8a986-121">Pro předdefinované číselné typy implicitní převod může vzít v úvahu hodnota, která má být uložen se vejde do proměnné bez zkrácen nebo zaokrouhleno.</span><span class="sxs-lookup"><span data-stu-id="8a986-121">For built-in numeric types, an implicit conversion can be made when the value to be stored can fit into the variable without being truncated or rounded off.</span></span> <span data-ttu-id="8a986-122">Například proměnná typu [dlouhé](../../../csharp/language-reference/keywords/long.md) (64bitové celé číslo) můžete ukládat některá hodnota, která [int](../../../csharp/language-reference/keywords/int.md) (32bitové celé číslo) můžete ukládat.</span><span class="sxs-lookup"><span data-stu-id="8a986-122">For example, a variable of type [long](../../../csharp/language-reference/keywords/long.md) (64-bit integer) can store any value that an [int](../../../csharp/language-reference/keywords/int.md) (32-bit integer) can store.</span></span> <span data-ttu-id="8a986-123">V následujícím příkladu kompilátor implicitně převede hodnotu `num` na pravé straně na typ `long` před ji přiřadíte `bigNum`.</span><span class="sxs-lookup"><span data-stu-id="8a986-123">In the following example, the compiler implicitly converts the value of `num` on the right to a type `long` before assigning it to `bigNum`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#34)]  
  
 <span data-ttu-id="8a986-124">Úplný seznam všech implicitních číselných převodů, naleznete v tématu [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="8a986-124">For a complete list of all implicit numeric conversions, see [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
 <span data-ttu-id="8a986-125">Pro typy odkazů existuje vždy implicitní převod z třídy na některý z jeho přímou nebo nepřímou základní třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8a986-125">For reference types, an implicit conversion always exists from a class to any one of its direct or indirect base classes or interfaces.</span></span> <span data-ttu-id="8a986-126">Žádná speciální syntax je nezbytné, protože odvozené třídy vždy obsahuje všechny členy základní třídy.</span><span class="sxs-lookup"><span data-stu-id="8a986-126">No special syntax is necessary because a derived class always contains all the members of a base class.</span></span>  
  
```  
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a><span data-ttu-id="8a986-127">Explicitní převody</span><span class="sxs-lookup"><span data-stu-id="8a986-127">Explicit conversions</span></span>

 <span data-ttu-id="8a986-128">Nicméně, pokud převod nelze provést bez rizika ztráty informací, kompilátor vyžaduje, abyste provedli explicitní převod, která je volána *přetypování*.</span><span class="sxs-lookup"><span data-stu-id="8a986-128">However, if a conversion cannot be made without a risk of losing information, the compiler requires that you perform an explicit conversion, which is called a *cast*.</span></span> <span data-ttu-id="8a986-129">Přetypování je způsob, jak explicitně informuje kompilátor, že máte v úmyslu provést převod a že jste si vědomi, že může dojít ke ztrátě dat.</span><span class="sxs-lookup"><span data-stu-id="8a986-129">A cast is a way of explicitly informing the compiler that you intend to make the conversion and that you are aware that data loss might occur.</span></span> <span data-ttu-id="8a986-130">K provedení přetypování, zadejte, která jsou přetypování na typ v závorkách před hodnota nebo proměnná, která má být převeden.</span><span class="sxs-lookup"><span data-stu-id="8a986-130">To perform a cast, specify the type that you are casting to in parentheses in front of the value or variable to be converted.</span></span> <span data-ttu-id="8a986-131">Následující program přetypování [double](../../../csharp/language-reference/keywords/double.md) do [int](../../../csharp/language-reference/keywords/int.md). Program nebude kompilovat bez přetypování.</span><span class="sxs-lookup"><span data-stu-id="8a986-131">The following program casts a [double](../../../csharp/language-reference/keywords/double.md) to an [int](../../../csharp/language-reference/keywords/int.md). The program will not compile without the cast.</span></span>  
  
 [!code-csharp[csProgGuideTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#2)]  
  
 <span data-ttu-id="8a986-132">Seznam explicitních číselných převodů, které jsou povoleny, naleznete v tématu [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="8a986-132">For a list of the explicit numeric conversions that are allowed, see [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span></span>  
  
 <span data-ttu-id="8a986-133">Pro typy odkazů se vyžaduje explicitní přetypování, pokud je potřeba převést ze základního typu odvozeného typu:</span><span class="sxs-lookup"><span data-stu-id="8a986-133">For reference types, an explicit cast is required if you need to convert from a base type to a derived type:</span></span>  
  
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
  
 <span data-ttu-id="8a986-134">Operace přetypování mezi typy odkazů nezmění běhového typu základního objektu; pouze změní typ hodnoty, který se používá jako odkaz na tento objekt.</span><span class="sxs-lookup"><span data-stu-id="8a986-134">A cast operation between reference types does not change the run-time type of the underlying object; it only changes the type of the value that is being used as a reference to that object.</span></span> <span data-ttu-id="8a986-135">Další informace najdete v tématu [polymorfismus](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).</span><span class="sxs-lookup"><span data-stu-id="8a986-135">For more information, see [Polymorphism](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).</span></span>  
  
## <a name="type-conversion-exceptions-at-run-time"></a><span data-ttu-id="8a986-136">Typ převodu výjimky za běhu</span><span class="sxs-lookup"><span data-stu-id="8a986-136">Type conversion exceptions at run time</span></span>

 <span data-ttu-id="8a986-137">V některých převodům typu odkaz kompilátor nemůže určit, zda bude platit přetypování.</span><span class="sxs-lookup"><span data-stu-id="8a986-137">In some reference type conversions, the compiler cannot determine whether a cast will be valid.</span></span> <span data-ttu-id="8a986-138">Je možné pro operace přetypování, které se správně zkompiluje selže v době běhu.</span><span class="sxs-lookup"><span data-stu-id="8a986-138">It is possible for a cast operation that compiles correctly to fail at run time.</span></span> <span data-ttu-id="8a986-139">Jak je znázorněno v následujícím příkladu, typu přetypování, že selže v době běhu způsobí, že <xref:System.InvalidCastException> vyvolání.</span><span class="sxs-lookup"><span data-stu-id="8a986-139">As shown in the following example, a type cast that fails at run time will cause an <xref:System.InvalidCastException> to be thrown.</span></span>  
  
 [!code-csharp[csProgGuideTypes#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#41)]  
  
 <span data-ttu-id="8a986-140">Jazyk C# poskytuje [je](../../../csharp/language-reference/keywords/is.md) a [jako](../../../csharp/language-reference/keywords/as.md) operátory umožňující testování kompatibility ve skutečnosti neodkazujícím přetypování.</span><span class="sxs-lookup"><span data-stu-id="8a986-140">C# provides the [is](../../../csharp/language-reference/keywords/is.md) and [as](../../../csharp/language-reference/keywords/as.md) operators to enable you to test for compatibility before actually performing a cast.</span></span> <span data-ttu-id="8a986-141">Další informace najdete v tématu [jak: Bezpečné přetypování pomocí porovnávání vzorů, jako je operátory](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).</span><span class="sxs-lookup"><span data-stu-id="8a986-141">For more information, see [How to: Safely cast using pattern matching, as and is Operators](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="8a986-142">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8a986-142">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a><span data-ttu-id="8a986-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a986-143">See also</span></span>

- [<span data-ttu-id="8a986-144">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8a986-144">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="8a986-145">Typy</span><span class="sxs-lookup"><span data-stu-id="8a986-145">Types</span></span>](../../../csharp/programming-guide/types/index.md)
- [<span data-ttu-id="8a986-146">() – operátor</span><span class="sxs-lookup"><span data-stu-id="8a986-146">() Operator</span></span>](../../../csharp/language-reference/operators/invocation-operator.md)
- [<span data-ttu-id="8a986-147">explicit</span><span class="sxs-lookup"><span data-stu-id="8a986-147">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)
- [<span data-ttu-id="8a986-148">implicit</span><span class="sxs-lookup"><span data-stu-id="8a986-148">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)
- [<span data-ttu-id="8a986-149">Operátory převodu</span><span class="sxs-lookup"><span data-stu-id="8a986-149">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
- <span data-ttu-id="8a986-150">[Převod zobecněného typu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/yy580hbd(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="8a986-150">[Generalized Type Conversion](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/yy580hbd(v=vs.120))</span></span>
- [<span data-ttu-id="8a986-151">Postupy: Převod řetězce na číslo</span><span class="sxs-lookup"><span data-stu-id="8a986-151">How to: Convert a String to a Number</span></span>](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)
