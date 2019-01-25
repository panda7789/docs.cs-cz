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
ms.openlocfilehash: 2f09a2842edfa9471267f294c9b64229ae824098
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738745"
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="59065-102">Typy hodnot a typy odkazu</span><span class="sxs-lookup"><span data-stu-id="59065-102">Value Types and Reference Types</span></span>
<span data-ttu-id="59065-103">Datové typy v jazyce Visual Basic jsou implementovány podle jejich klasifikace.</span><span class="sxs-lookup"><span data-stu-id="59065-103">In Visual Basic, data types are implemented based on their classification.</span></span> <span data-ttu-id="59065-104">Datové typy jazyka Visual Basic lze rozdělit podle Určuje, zda proměnná určitého typu ukládá svoje vlastní data nebo ukazatel na data.</span><span class="sxs-lookup"><span data-stu-id="59065-104">The Visual Basic data types can be classified according to whether a variable of a particular type stores its own data or a pointer to the data.</span></span> <span data-ttu-id="59065-105">Pokud ukládá svoje vlastní data *typ hodnoty*; pokud drží ukazatel na data jinde v paměti je *odkazovat na typ*.</span><span class="sxs-lookup"><span data-stu-id="59065-105">If it stores its own data it is a *value type*; if it holds a pointer to data elsewhere in memory it is a *reference type*.</span></span>  
  
## <a name="value-types"></a><span data-ttu-id="59065-106">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="59065-106">Value Types</span></span>  
 <span data-ttu-id="59065-107">Datový typ je *typ hodnoty* pokud obsahuje data v rámci své vlastní přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="59065-107">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="59065-108">Typy hodnot patří:</span><span class="sxs-lookup"><span data-stu-id="59065-108">Value types include the following:</span></span>  
  
-   <span data-ttu-id="59065-109">Všechny číselné datové typy</span><span class="sxs-lookup"><span data-stu-id="59065-109">All numeric data types</span></span>  
  
-   <span data-ttu-id="59065-110">`Boolean`, `Char`, a `Date`</span><span class="sxs-lookup"><span data-stu-id="59065-110">`Boolean`, `Char`, and `Date`</span></span>  
  
-   <span data-ttu-id="59065-111">Všechny struktury, i když jejich členové jsou odkazové typy</span><span class="sxs-lookup"><span data-stu-id="59065-111">All structures, even if their members are reference types</span></span>  
  
-   <span data-ttu-id="59065-112">Výčty, protože jeho základní typ je vždy `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, nebo `ULong`</span><span class="sxs-lookup"><span data-stu-id="59065-112">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="59065-113">Každý struktura je typ hodnoty, i v případě, že obsahuje členy typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="59065-113">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="59065-114">Z tohoto důvodu hodnotové typy, jako `Char` a `Integer` implementují struktury rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="59065-114">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="59065-115">Typ hodnoty je možné deklarovat pomocí vyhrazené slovo, například `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="59065-115">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="59065-116">Můžete také použít `New` – klíčové slovo k inicializaci typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="59065-116">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="59065-117">To je obzvláště užitečné, pokud typ má konstruktor, který používá parametry.</span><span class="sxs-lookup"><span data-stu-id="59065-117">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="59065-118">Příkladem je <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> konstruktor, který vytvoří nový `Decimal` hodnotu ze zadaného částí.</span><span class="sxs-lookup"><span data-stu-id="59065-118">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="59065-119">Typy odkazů</span><span class="sxs-lookup"><span data-stu-id="59065-119">Reference Types</span></span>  
 <span data-ttu-id="59065-120">A *odkazovat na typ* obsahuje ukazatel do jiného umístění v paměti, která obsahuje data.</span><span class="sxs-lookup"><span data-stu-id="59065-120">A *reference type* contains a pointer to another memory location that holds the data.</span></span> <span data-ttu-id="59065-121">Odkazové typy zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="59065-121">Reference types include the following:</span></span>  
  
-   `String`  
  
-   <span data-ttu-id="59065-122">Všechna pole, i když jsou jejich prvky typy hodnot</span><span class="sxs-lookup"><span data-stu-id="59065-122">All arrays, even if their elements are value types</span></span>  
  
-   <span data-ttu-id="59065-123">Typy, jako například tříd <xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="59065-123">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
-   <span data-ttu-id="59065-124">Delegáty</span><span class="sxs-lookup"><span data-stu-id="59065-124">Delegates</span></span>  
  
 <span data-ttu-id="59065-125">Třída je *odkazovat na typ*.</span><span class="sxs-lookup"><span data-stu-id="59065-125">A class is a *reference type*.</span></span> <span data-ttu-id="59065-126">Z tohoto důvodu referenční typy `Object` a `String` podporují [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] třídy.</span><span class="sxs-lookup"><span data-stu-id="59065-126">For this reason, reference types such as `Object` and `String` are supported by [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes.</span></span> <span data-ttu-id="59065-127">Upozorňujeme, že každé pole typu odkazu, i v případě, že její členy jsou typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="59065-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="59065-128">Protože každý odkaz na typ představuje základní třídy rozhraní .NET Framework, je nutné použít [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md) – klíčové slovo je inicializovat.</span><span class="sxs-lookup"><span data-stu-id="59065-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="59065-129">Následující příkaz inicializuje pole.</span><span class="sxs-lookup"><span data-stu-id="59065-129">The following statement initializes an array.</span></span>  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="59065-130">Prvky, které nejsou typy</span><span class="sxs-lookup"><span data-stu-id="59065-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="59065-131">Následující programovací prvky nekvalifikujte jako typy, protože některý z nich nelze zadat pro element deklarovaný typ dat:</span><span class="sxs-lookup"><span data-stu-id="59065-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
-   <span data-ttu-id="59065-132">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="59065-132">Namespaces</span></span>  
  
-   <span data-ttu-id="59065-133">Moduly</span><span class="sxs-lookup"><span data-stu-id="59065-133">Modules</span></span>  
  
-   <span data-ttu-id="59065-134">Události</span><span class="sxs-lookup"><span data-stu-id="59065-134">Events</span></span>  
  
-   <span data-ttu-id="59065-135">Vlastnosti a postupy</span><span class="sxs-lookup"><span data-stu-id="59065-135">Properties and procedures</span></span>  
  
-   <span data-ttu-id="59065-136">Proměnné, konstanty a pole</span><span class="sxs-lookup"><span data-stu-id="59065-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="59065-137">Práce s datovým typem objektu</span><span class="sxs-lookup"><span data-stu-id="59065-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="59065-138">Proměnné můžete přiřadit odkazový typ nebo hodnotový typ `Object` datového typu.</span><span class="sxs-lookup"><span data-stu-id="59065-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="59065-139">`Object` Proměnnou vždy obsahuje ukazatel na data, nikdy vlastní data.</span><span class="sxs-lookup"><span data-stu-id="59065-139">An `Object` variable always holds a pointer to the data, never the data itself.</span></span> <span data-ttu-id="59065-140">Nicméně pokud přiřadíte typ hodnoty do `Object` proměnné, se chová jako obsahuje vlastní data.</span><span class="sxs-lookup"><span data-stu-id="59065-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="59065-141">Další informace najdete v tématu [datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="59065-141">For more information, see [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="59065-142">Můžete zjistit, jestli se `Object` proměnné funguje jako odkaz na typ nebo hodnotový typ ji do <xref:Microsoft.VisualBasic.Information.IsReference%2A> metoda ve <xref:Microsoft.VisualBasic.Information> třídu <xref:Microsoft.VisualBasic?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="59065-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="59065-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> Vrátí `True` Pokud obsah `Object` proměnná představuje typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="59065-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59065-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59065-144">See also</span></span>
- [<span data-ttu-id="59065-145">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="59065-145">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="59065-146">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="59065-146">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="59065-147">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="59065-147">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="59065-148">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="59065-148">Efficient Use of Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="59065-149">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="59065-149">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="59065-150">Datové typy</span><span class="sxs-lookup"><span data-stu-id="59065-150">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
