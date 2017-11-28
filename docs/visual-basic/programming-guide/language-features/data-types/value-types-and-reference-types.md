---
title: Typy hodnot a typy odkazu
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- reference data types [Visual Basic]
- reference types [Visual Basic]
- value types [Visual Basic]
- value data types [Visual Basic]
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2b54945d27d186771e8b5353e753afd74c56d71b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="a3442-102">Typy hodnot a typy odkazu</span><span class="sxs-lookup"><span data-stu-id="a3442-102">Value Types and Reference Types</span></span>
<span data-ttu-id="a3442-103">V jazyce Visual Basic – datové typy jsou implementované podle jejich klasifikace.</span><span class="sxs-lookup"><span data-stu-id="a3442-103">In Visual Basic, data types are implemented based on their classification.</span></span> <span data-ttu-id="a3442-104">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Datové typy můžou být klasifikované podle jestli proměnné určitého typu ukládá svá vlastní data nebo odkazy na data.</span><span class="sxs-lookup"><span data-stu-id="a3442-104">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types can be classified according to whether a variable of a particular type stores its own data or a pointer to the data.</span></span> <span data-ttu-id="a3442-105">Pokud ukládají svá vlastní data *typ hodnoty*; Pokud má ukazatel na data jinde v paměti je *odkazují na typ*.</span><span class="sxs-lookup"><span data-stu-id="a3442-105">If it stores its own data it is a *value type*; if it holds a pointer to data elsewhere in memory it is a *reference type*.</span></span>  
  
## <a name="value-types"></a><span data-ttu-id="a3442-106">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="a3442-106">Value Types</span></span>  
 <span data-ttu-id="a3442-107">Datový typ *typ hodnoty* pokud drží dat v rámci vlastní přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="a3442-107">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="a3442-108">Typy hodnot zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="a3442-108">Value types include the following:</span></span>  
  
-   <span data-ttu-id="a3442-109">Všechny číselné datové typy</span><span class="sxs-lookup"><span data-stu-id="a3442-109">All numeric data types</span></span>  
  
-   <span data-ttu-id="a3442-110">`Boolean`, `Char`, a`Date`</span><span class="sxs-lookup"><span data-stu-id="a3442-110">`Boolean`, `Char`, and `Date`</span></span>  
  
-   <span data-ttu-id="a3442-111">Všechny struktury, i když jsou jejich členové odkazové typy</span><span class="sxs-lookup"><span data-stu-id="a3442-111">All structures, even if their members are reference types</span></span>  
  
-   <span data-ttu-id="a3442-112">Výčty, protože jejich základní typ je vždy `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, nebo`ULong`</span><span class="sxs-lookup"><span data-stu-id="a3442-112">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="a3442-113">Každý struktura je hodnota typu, i v případě, že obsahuje členy typu odkaz.</span><span class="sxs-lookup"><span data-stu-id="a3442-113">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="a3442-114">Z tohoto důvodu, hodnotu, jako typy `Char` a `Integer` jsou implementované struktury rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a3442-114">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="a3442-115">Typ hodnoty můžou deklarovat pomocí vyhrazené slovo, například `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="a3442-115">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="a3442-116">Můžete také `New` – klíčové slovo k chybě při inicializaci typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a3442-116">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="a3442-117">To je obzvláště užitečné, pokud má tento typ konstruktor, který používá parametry.</span><span class="sxs-lookup"><span data-stu-id="a3442-117">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="a3442-118">Příkladem je <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> konstruktor, který vytvoří nový `Decimal` hodnotu z části zadaný.</span><span class="sxs-lookup"><span data-stu-id="a3442-118">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="a3442-119">Typy odkazů</span><span class="sxs-lookup"><span data-stu-id="a3442-119">Reference Types</span></span>  
 <span data-ttu-id="a3442-120">A *odkazují na typ* obsahuje ukazatel do jiného umístění paměti, která obsahuje data.</span><span class="sxs-lookup"><span data-stu-id="a3442-120">A *reference type* contains a pointer to another memory location that holds the data.</span></span> <span data-ttu-id="a3442-121">Odkazové typy patří:</span><span class="sxs-lookup"><span data-stu-id="a3442-121">Reference types include the following:</span></span>  
  
-   `String`  
  
-   <span data-ttu-id="a3442-122">Všechna pole, i když jejich prvky jsou typy hodnot</span><span class="sxs-lookup"><span data-stu-id="a3442-122">All arrays, even if their elements are value types</span></span>  
  
-   <span data-ttu-id="a3442-123">Typy tříd, jako například<xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="a3442-123">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
-   <span data-ttu-id="a3442-124">Delegáty</span><span class="sxs-lookup"><span data-stu-id="a3442-124">Delegates</span></span>  
  
 <span data-ttu-id="a3442-125">Třída je *odkazují na typ*.</span><span class="sxs-lookup"><span data-stu-id="a3442-125">A class is a *reference type*.</span></span> <span data-ttu-id="a3442-126">Z tohoto důvodu odkazové typy `Object` a `String` podporuje [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] třídy.</span><span class="sxs-lookup"><span data-stu-id="a3442-126">For this reason, reference types such as `Object` and `String` are supported by [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes.</span></span> <span data-ttu-id="a3442-127">Všimněte si, že každé pole je typu odkazu. i v případě jeho členové jsou typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="a3442-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="a3442-128">Vzhledem k tomu, že každý typ odkazu představuje základní třídu rozhraní .NET Framework, je nutné použít [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md) – klíčové slovo provést jeho inicializaci.</span><span class="sxs-lookup"><span data-stu-id="a3442-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="a3442-129">Následující příkaz inicializuje pole.</span><span class="sxs-lookup"><span data-stu-id="a3442-129">The following statement initializes an array.</span></span>  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="a3442-130">Elementy, které nejsou typy</span><span class="sxs-lookup"><span data-stu-id="a3442-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="a3442-131">Následující elementům programování nemohou být jako typy, protože některý z nich nelze zadat jako datový typ pro element deklarované:</span><span class="sxs-lookup"><span data-stu-id="a3442-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
-   <span data-ttu-id="a3442-132">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="a3442-132">Namespaces</span></span>  
  
-   <span data-ttu-id="a3442-133">Moduly</span><span class="sxs-lookup"><span data-stu-id="a3442-133">Modules</span></span>  
  
-   <span data-ttu-id="a3442-134">Události</span><span class="sxs-lookup"><span data-stu-id="a3442-134">Events</span></span>  
  
-   <span data-ttu-id="a3442-135">Vlastnosti a postupy</span><span class="sxs-lookup"><span data-stu-id="a3442-135">Properties and procedures</span></span>  
  
-   <span data-ttu-id="a3442-136">Pole, konstanty a proměnné</span><span class="sxs-lookup"><span data-stu-id="a3442-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="a3442-137">Práce s datovým typem objektu</span><span class="sxs-lookup"><span data-stu-id="a3442-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="a3442-138">Proměnné můžete přiřadit odkazového typu nebo typ hodnoty `Object` datového typu.</span><span class="sxs-lookup"><span data-stu-id="a3442-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="a3442-139">`Object` Proměnné vždy obsahuje ukazatel k datům, nikdy samotná data.</span><span class="sxs-lookup"><span data-stu-id="a3442-139">An `Object` variable always holds a pointer to the data, never the data itself.</span></span> <span data-ttu-id="a3442-140">Ale pokud přiřadíte typ hodnoty do `Object` proměnné, chová jako kdyby drží svá vlastní data.</span><span class="sxs-lookup"><span data-stu-id="a3442-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="a3442-141">Další informace najdete v tématu [Object – datový typ](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="a3442-141">For more information, see [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="a3442-142">Můžete zjistit, jestli se `Object` proměnná funguje jako odkaz na typ nebo typ hodnoty předáním jeho <xref:Microsoft.VisualBasic.Information.IsReference%2A> metoda v <xref:Microsoft.VisualBasic.Information> třídu <xref:Microsoft.VisualBasic?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a3442-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="a3442-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType>Vrátí `True` Pokud obsah `Object` proměnná představuje odkazového typu.</span><span class="sxs-lookup"><span data-stu-id="a3442-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3442-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="a3442-144">See Also</span></span>  
 [<span data-ttu-id="a3442-145">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="a3442-145">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="a3442-146">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a3442-146">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="a3442-147">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="a3442-147">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="a3442-148">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="a3442-148">Efficient Use of Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="a3442-149">Object – datový typ</span><span class="sxs-lookup"><span data-stu-id="a3442-149">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="a3442-150">Datové typy</span><span class="sxs-lookup"><span data-stu-id="a3442-150">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
