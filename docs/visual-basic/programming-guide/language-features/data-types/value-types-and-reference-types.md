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
ms.openlocfilehash: 3a1de120f5f97ba93939f332f121d70cd3091216
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392971"
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="3ed8b-102">Typy hodnot a typy odkazu</span><span class="sxs-lookup"><span data-stu-id="3ed8b-102">Value Types and Reference Types</span></span>
<span data-ttu-id="3ed8b-103">Existují dva druhy typů v Visual Basic: typy odkazu a typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="3ed8b-103">There are two kinds of types in Visual Basic: reference types and value types.</span></span> <span data-ttu-id="3ed8b-104">Proměnné typů odkazu ukládají odkazy na data (objekty), zatímco proměnné typů hodnoty data přímo obsahují příslušná data.</span><span class="sxs-lookup"><span data-stu-id="3ed8b-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="3ed8b-105">V případě typů odkazu mohou dvě proměnné odkazovat na stejný objekt. Operace v rámci jedné proměnné tedy mohou ovlivňovat objekt odkazovaný jinou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="3ed8b-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="3ed8b-106">S typy hodnot každá proměnná má svou vlastní kopii dat a není možné, aby operace s jednou proměnnou ovlivnily jiný (kromě případu, kdy [Modifikátor ByRef u parametrů](../../../language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="3ed8b-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of the [ByRef modifier on parameters](../../../language-reference/modifiers/byref.md)).</span></span>
  
## <a name="value-types"></a><span data-ttu-id="3ed8b-107">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="3ed8b-107">Value Types</span></span>  
 <span data-ttu-id="3ed8b-108">Datový typ je *typ hodnoty* , pokud obsahuje data v rámci své vlastní alokace paměti.</span><span class="sxs-lookup"><span data-stu-id="3ed8b-108">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="3ed8b-109">Typy hodnot zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="3ed8b-109">Value types include the following:</span></span>  
  
- <span data-ttu-id="3ed8b-110">Všechny číselné datové typy</span><span class="sxs-lookup"><span data-stu-id="3ed8b-110">All numeric data types</span></span>  
  
- <span data-ttu-id="3ed8b-111">`Boolean`, `Char` a`Date`</span><span class="sxs-lookup"><span data-stu-id="3ed8b-111">`Boolean`, `Char`, and `Date`</span></span>  
  
- <span data-ttu-id="3ed8b-112">Všechny struktury, i když jejich členové jsou odkazové typy</span><span class="sxs-lookup"><span data-stu-id="3ed8b-112">All structures, even if their members are reference types</span></span>  
  
- <span data-ttu-id="3ed8b-113">Výčty, protože jejich nadřízený typ je vždy `SByte` , `Short` , `Integer` , `Long` , `Byte` , `UShort` , `UInteger` nebo`ULong`</span><span class="sxs-lookup"><span data-stu-id="3ed8b-113">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="3ed8b-114">Každá struktura je typ hodnoty, a to i v případě, že obsahuje členy typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="3ed8b-114">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="3ed8b-115">Z tohoto důvodu jsou typy hodnot jako `Char` a `Integer` implementovány .NET Framework struktury.</span><span class="sxs-lookup"><span data-stu-id="3ed8b-115">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="3ed8b-116">Typ hodnoty lze deklarovat pomocí klíčového slova rezervované, například `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="3ed8b-116">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="3ed8b-117">Můžete také použít `New` klíčové slovo k inicializaci typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3ed8b-117">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="3ed8b-118">To je užitečné hlavně v případě, že typ má konstruktor, který přebírá parametry.</span><span class="sxs-lookup"><span data-stu-id="3ed8b-118">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="3ed8b-119">Příkladem je <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> konstruktor, který vytváří novou `Decimal` hodnotu ze zadaných částí.</span><span class="sxs-lookup"><span data-stu-id="3ed8b-119">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="3ed8b-120">Typy odkazů</span><span class="sxs-lookup"><span data-stu-id="3ed8b-120">Reference Types</span></span>  
 <span data-ttu-id="3ed8b-121">*Odkazový typ* ukládá odkaz na jeho data.</span><span class="sxs-lookup"><span data-stu-id="3ed8b-121">A *reference type* stores a reference to its data.</span></span> <span data-ttu-id="3ed8b-122">Typy odkazů zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="3ed8b-122">Reference types include the following:</span></span>  
  
- `String`  
  
- <span data-ttu-id="3ed8b-123">Všechna pole, i když jejich prvky jsou typy hodnot</span><span class="sxs-lookup"><span data-stu-id="3ed8b-123">All arrays, even if their elements are value types</span></span>  
  
- <span data-ttu-id="3ed8b-124">Typy tříd, jako např.<xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="3ed8b-124">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
- <span data-ttu-id="3ed8b-125">Delegáti</span><span class="sxs-lookup"><span data-stu-id="3ed8b-125">Delegates</span></span>  
  
 <span data-ttu-id="3ed8b-126">Třída je *odkazový typ*.</span><span class="sxs-lookup"><span data-stu-id="3ed8b-126">A class is a *reference type*.</span></span> <span data-ttu-id="3ed8b-127">Všimněte si, že každé pole je typ odkazu, a to i v případě, že jeho členy jsou typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="3ed8b-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="3ed8b-128">Vzhledem k tomu, že každý typ odkazu představuje základní třídu .NET Framework, je nutné při inicializaci použít klíčové slovo [New operátor](../../../language-reference/operators/new-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="3ed8b-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="3ed8b-129">Následující příkaz inicializuje pole.</span><span class="sxs-lookup"><span data-stu-id="3ed8b-129">The following statement initializes an array.</span></span>  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="3ed8b-130">Prvky, které nejsou typy</span><span class="sxs-lookup"><span data-stu-id="3ed8b-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="3ed8b-131">Následující programovací prvky neopravňují jako typy, protože nemůžete zadat žádné z nich jako datový typ pro deklarovaný element:</span><span class="sxs-lookup"><span data-stu-id="3ed8b-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
- <span data-ttu-id="3ed8b-132">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="3ed8b-132">Namespaces</span></span>  
  
- <span data-ttu-id="3ed8b-133">Moduly</span><span class="sxs-lookup"><span data-stu-id="3ed8b-133">Modules</span></span>  
  
- <span data-ttu-id="3ed8b-134">Události</span><span class="sxs-lookup"><span data-stu-id="3ed8b-134">Events</span></span>  
  
- <span data-ttu-id="3ed8b-135">Vlastnosti a procedury</span><span class="sxs-lookup"><span data-stu-id="3ed8b-135">Properties and procedures</span></span>  
  
- <span data-ttu-id="3ed8b-136">Proměnné, konstanty a pole</span><span class="sxs-lookup"><span data-stu-id="3ed8b-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="3ed8b-137">Práce s datovým typem objektu</span><span class="sxs-lookup"><span data-stu-id="3ed8b-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="3ed8b-138">Proměnné datového typu můžete přiřadit buď odkazový typ, nebo typ hodnoty `Object` .</span><span class="sxs-lookup"><span data-stu-id="3ed8b-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="3ed8b-139">`Object`Proměnná vždy obsahuje odkaz na data, ale samotná data.</span><span class="sxs-lookup"><span data-stu-id="3ed8b-139">An `Object` variable always holds a reference to the data, never the data itself.</span></span> <span data-ttu-id="3ed8b-140">Pokud však přiřadíte typ hodnoty `Object` proměnné, bude se chovat jako, pokud obsahuje vlastní data.</span><span class="sxs-lookup"><span data-stu-id="3ed8b-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="3ed8b-141">Další informace najdete v tématu [datový typ Object](../../../language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="3ed8b-141">For more information, see [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="3ed8b-142">Můžete zjistit, zda proměnná funguje `Object` jako typ odkazu nebo typ hodnoty předáním do <xref:Microsoft.VisualBasic.Information.IsReference%2A> metody ve <xref:Microsoft.VisualBasic.Information> třídě <xref:Microsoft.VisualBasic?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3ed8b-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="3ed8b-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType>Vrátí, `True` zda obsah `Object` proměnné představuje typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="3ed8b-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ed8b-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ed8b-144">See also</span></span>

- [<span data-ttu-id="3ed8b-145">Typy hodnot s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="3ed8b-145">Nullable Value Types</span></span>](nullable-value-types.md)
- [<span data-ttu-id="3ed8b-146">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3ed8b-146">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="3ed8b-147">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="3ed8b-147">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="3ed8b-148">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="3ed8b-148">Efficient Use of Data Types</span></span>](efficient-use-of-data-types.md)
- [<span data-ttu-id="3ed8b-149">Datový typ objektu</span><span class="sxs-lookup"><span data-stu-id="3ed8b-149">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="3ed8b-150">Datové typy</span><span class="sxs-lookup"><span data-stu-id="3ed8b-150">Data Types</span></span>](index.md)
