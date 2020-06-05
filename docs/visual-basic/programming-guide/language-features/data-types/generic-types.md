---
title: Obecné typy
ms.date: 07/20/2015
helpviewer_keywords:
- generic interfaces
- data type arguments [Visual Basic], defining
- generic delegates
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- delegates, generic
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- procedures [Visual Basic], generic
- generic procedures
- data types [Visual Basic], generic
- data types [Visual Basic], as parameters
- generics [Visual Basic], generic types
- data types [Visual Basic], as arguments
- generic classes [Visual Basic], Visual Basic
- parameters [Visual Basic], type
- type arguments
- interfaces [Visual Basic], generic
- generics [Visual Basic]
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generic structures [Visual Basic]
- generic classes [Visual Basic]
- type parameters
- data type arguments
- structures [Visual Basic], generic
- parameters [Visual Basic], data type
- collections, generic
- classes [Visual Basic], generic
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 89f771d9-ecbb-4737-88b8-116b63c6cf4d
ms.openlocfilehash: b14c7a3f1f667e7c13ec0ae46185ed3ece92beb8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394049"
---
# <a name="generic-types-in-visual-basic-visual-basic"></a><span data-ttu-id="1bbcf-102">Obecné typy v jazyce Visual Basic (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bbcf-102">Generic Types in Visual Basic (Visual Basic)</span></span>
<span data-ttu-id="1bbcf-103">*Obecný typ* je jediný programovací prvek, který se přizpůsobí tak, aby prováděl stejnou funkčnost pro celou řadu datových typů.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-103">A *generic type* is a single programming element that adapts to perform the same functionality for a variety of data types.</span></span> <span data-ttu-id="1bbcf-104">Při definování obecné třídy nebo procedury není nutné definovat samostatnou verzi pro každý datový typ, pro který byste mohli chtít tuto funkci provést.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-104">When you define a generic class or procedure, you do not have to define a separate version for each data type for which you might want to perform that functionality.</span></span>  
  
 <span data-ttu-id="1bbcf-105">Analogie je Screwdriver sada s vyměnitelnými hlavami.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-105">An analogy is a screwdriver set with removable heads.</span></span> <span data-ttu-id="1bbcf-106">Kontrolujete šroub, který potřebujete, abyste mohli zapnout a vybrat správnou hlavu pro daný šroub (s drážkou, překříženým označených hvězdičkou).</span><span class="sxs-lookup"><span data-stu-id="1bbcf-106">You inspect the screw you need to turn and select the correct head for that screw (slotted, crossed, starred).</span></span> <span data-ttu-id="1bbcf-107">Po vložení správného záhlaví v popisovači Screwdriver provedete přesnou stejnou funkci s Screwdriver, a to tak, že zapnete šroub.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-107">Once you insert the correct head in the screwdriver handle, you perform the exact same function with the screwdriver, namely turning the screw.</span></span>  
  
 ![Diagram Screwdriver sady s různými hlavami](./media/generic-types/generic-screwdriver-set.gif)  
  
 <span data-ttu-id="1bbcf-109">Definujete-li obecný typ, můžete ho parametrizovat pomocí jednoho nebo více datových typů.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-109">When you define a generic type, you parameterize it with one or more data types.</span></span> <span data-ttu-id="1bbcf-110">To umožňuje, aby kód používal k přizpůsobení datových typů požadavkům.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-110">This allows the using code to tailor the data types to its requirements.</span></span> <span data-ttu-id="1bbcf-111">Váš kód může deklarovat několik různých programovacích prvků z obecného prvku, každý z nich působí na jinou sadu datových typů.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-111">Your code can declare several different programming elements from the generic element, each one acting on a different set of data types.</span></span> <span data-ttu-id="1bbcf-112">Ale deklarované prvky všechny provádějí stejnou logiku bez ohledu na to, jaké typy dat používají.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-112">But the declared elements all perform the identical logic, no matter what data types they are using.</span></span>  
  
 <span data-ttu-id="1bbcf-113">Například můžete chtít vytvořit a použít třídu fronty, která pracuje na konkrétním datovém typu, jako je například `String` .</span><span class="sxs-lookup"><span data-stu-id="1bbcf-113">For example, you might want to create and use a queue class that operates on a specific data type such as `String`.</span></span> <span data-ttu-id="1bbcf-114">Takovou třídu můžete deklarovat z <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> , jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-114">You can declare such a class from <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#1)]  
  
 <span data-ttu-id="1bbcf-115">Nyní můžete použít `stringQ` výhradně pro práci s `String` hodnotami.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-115">You can now use `stringQ` to work exclusively with `String` values.</span></span> <span data-ttu-id="1bbcf-116">Vzhledem `stringQ` k tomu, že je specifická pro `String` místo generalizace pro `Object` hodnoty, nemáte pozdní vazbu nebo převod typu.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-116">Because `stringQ` is specific for `String` instead of being generalized for `Object` values, you do not have late binding or type conversion.</span></span> <span data-ttu-id="1bbcf-117">Tím se ušetří čas spuštění a zkracuje se běhové chyby.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-117">This saves execution time and reduces run-time errors.</span></span>  
  
 <span data-ttu-id="1bbcf-118">Další informace o použití obecného typu naleznete v tématu [How to: Use a Generic Class](how-to-use-a-generic-class.md).</span><span class="sxs-lookup"><span data-stu-id="1bbcf-118">For more information on using a generic type, see [How to: Use a Generic Class](how-to-use-a-generic-class.md).</span></span>  
  
## <a name="example-of-a-generic-class"></a><span data-ttu-id="1bbcf-119">Příklad obecné třídy</span><span class="sxs-lookup"><span data-stu-id="1bbcf-119">Example of a Generic Class</span></span>  
 <span data-ttu-id="1bbcf-120">Následující příklad ukazuje kostru definice obecné třídy.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-120">The following example shows a skeleton definition of a generic class.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#2)]  
  
 <span data-ttu-id="1bbcf-121">V předchozí kostra `t` je *parametr typu*, tedy zástupný symbol pro datový typ, který zadáte při deklaraci třídy.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-121">In the preceding skeleton, `t` is a *type parameter*, that is, a placeholder for a data type that you supply when you declare the class.</span></span> <span data-ttu-id="1bbcf-122">Jinde v kódu můžete deklarovat různé verze nástroje `classHolder` zadáním různých datových typů pro `t` .</span><span class="sxs-lookup"><span data-stu-id="1bbcf-122">Elsewhere in your code, you can declare various versions of `classHolder` by supplying various data types for `t`.</span></span> <span data-ttu-id="1bbcf-123">Následující příklad ukazuje dvě takové deklarace.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-123">The following example shows two such declarations.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#3)]  
  
 <span data-ttu-id="1bbcf-124">Předchozí příkazy deklaruje *konstruované třídy*, ve kterých konkrétní typ nahradí parametr typu.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-124">The preceding statements declare *constructed classes*, in which a specific type replaces the type parameter.</span></span> <span data-ttu-id="1bbcf-125">Tato náhrada je šířena v celém kódu v rámci konstruované třídy.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-125">This replacement is propagated throughout the code within the constructed class.</span></span> <span data-ttu-id="1bbcf-126">Následující příklad ukazuje, jak `processNewItem` procedura vypadá jako v `integerClass` .</span><span class="sxs-lookup"><span data-stu-id="1bbcf-126">The following example shows what the `processNewItem` procedure looks like in `integerClass`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#4)]  
  
 <span data-ttu-id="1bbcf-127">Úplnější příklad naleznete v tématu [How to: define a Class, která může poskytovat identické funkce pro různé datové typy](how-to-define-a-class-that-can-provide-identical-functionality.md).</span><span class="sxs-lookup"><span data-stu-id="1bbcf-127">For a more complete example, see [How to: Define a Class That Can Provide Identical Functionality on Different Data Types](how-to-define-a-class-that-can-provide-identical-functionality.md).</span></span>  
  
## <a name="eligible-programming-elements"></a><span data-ttu-id="1bbcf-128">Oprávněné programovací prvky</span><span class="sxs-lookup"><span data-stu-id="1bbcf-128">Eligible Programming Elements</span></span>  
 <span data-ttu-id="1bbcf-129">Můžete definovat a používat obecné třídy, struktury, rozhraní, procedury a delegáty.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-129">You can define and use generic classes, structures, interfaces, procedures, and delegates.</span></span> <span data-ttu-id="1bbcf-130">Všimněte si, že .NET Framework definuje několik obecných tříd, struktur a rozhraní, které reprezentují běžně používané obecné prvky.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-130">Note that the .NET Framework defines several generic classes, structures, and interfaces that represent commonly used generic elements.</span></span> <span data-ttu-id="1bbcf-131"><xref:System.Collections.Generic?displayProperty=nameWithType>Obor názvů poskytuje slovníky, seznamy, fronty a zásobníky.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-131">The <xref:System.Collections.Generic?displayProperty=nameWithType> namespace provides dictionaries, lists, queues, and stacks.</span></span> <span data-ttu-id="1bbcf-132">Před definováním vlastního obecného prvku zkontrolujte, zda je již k dispozici v <xref:System.Collections.Generic?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1bbcf-132">Before defining your own generic element, see if it is already available in <xref:System.Collections.Generic?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="1bbcf-133">Procedury nejsou typy, ale můžete definovat a používat obecné procedury.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-133">Procedures are not types, but you can define and use generic procedures.</span></span> <span data-ttu-id="1bbcf-134">Viz [Obecné procedury v Visual Basic](generic-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1bbcf-134">See [Generic Procedures in Visual Basic](generic-procedures.md).</span></span>  
  
## <a name="advantages-of-generic-types"></a><span data-ttu-id="1bbcf-135">Výhody obecných typů</span><span class="sxs-lookup"><span data-stu-id="1bbcf-135">Advantages of Generic Types</span></span>  
 <span data-ttu-id="1bbcf-136">Obecný typ slouží jako základ pro deklarování několika různých programovacích prvků, z nichž každý pracuje na konkrétním datovém typu.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-136">A generic type serves as a basis for declaring several different programming elements, each of which operates on a specific data type.</span></span> <span data-ttu-id="1bbcf-137">Alternativy obecného typu jsou:</span><span class="sxs-lookup"><span data-stu-id="1bbcf-137">The alternatives to a generic type are:</span></span>  
  
1. <span data-ttu-id="1bbcf-138">Jeden typ, který pracuje na `Object` datovém typu.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-138">A single type operating on the `Object` data type.</span></span>  
  
2. <span data-ttu-id="1bbcf-139">Sada verzí typu *specifických pro konkrétní typ* , každá verze se individuálně nakóduje a pracuje na jednom konkrétním datovém typu, jako `String` je, `Integer` nebo uživatelem definovaný typ, jako je například `customer` .</span><span class="sxs-lookup"><span data-stu-id="1bbcf-139">A set of *type-specific* versions of the type, each version individually coded and operating on one specific data type such as `String`, `Integer`, or a user-defined type such as `customer`.</span></span>  
  
 <span data-ttu-id="1bbcf-140">Obecný typ má oproti těmto alternativám následující výhody:</span><span class="sxs-lookup"><span data-stu-id="1bbcf-140">A generic type has the following advantages over these alternatives:</span></span>  
  
- <span data-ttu-id="1bbcf-141">**Bezpečnost typů.**</span><span class="sxs-lookup"><span data-stu-id="1bbcf-141">**Type Safety.**</span></span> <span data-ttu-id="1bbcf-142">Obecné typy vynutily kontrolu typu při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-142">Generic types enforce compile-time type checking.</span></span> <span data-ttu-id="1bbcf-143">Typy založené na `Object` přijměte libovolný datový typ a musíte napsat kód, abyste zkontrolovali, jestli je vstupní datový typ přijatelný.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-143">Types based on `Object` accept any data type, and you must write code to check whether an input data type is acceptable.</span></span> <span data-ttu-id="1bbcf-144">S obecnými typy může kompilátor zachytit neshodu typu před časem spuštění.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-144">With generic types, the compiler can catch type mismatches before run time.</span></span>  
  
- <span data-ttu-id="1bbcf-145">**Předepsané.**</span><span class="sxs-lookup"><span data-stu-id="1bbcf-145">**Performance.**</span></span> <span data-ttu-id="1bbcf-146">Obecné typy nejsou k dispozici pro *pole* a *unbox* dat, protože každá z nich je specializovaná pro jeden datový typ.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-146">Generic types do not have to *box* and *unbox* data, because each one is specialized for one data type.</span></span> <span data-ttu-id="1bbcf-147">Operace založené na `Object` poli musí být vstupní datové typy, aby je bylo možné převést na `Object` data určená pro výstup a unbox je.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-147">Operations based on `Object` must box input data types to convert them to `Object` and unbox data destined for output.</span></span> <span data-ttu-id="1bbcf-148">Zabalení a rozbalení sníží výkon.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-148">Boxing and unboxing reduce performance.</span></span>  
  
     <span data-ttu-id="1bbcf-149">Typy založené na `Object` jsou také zpožděně vázány, což znamená, že přístup ke svým členům vyžaduje za běhu další kód.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-149">Types based on `Object` are also late-bound, which means that accessing their members requires extra code at run time.</span></span> <span data-ttu-id="1bbcf-150">Tím se také snižuje výkon.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-150">This also reduces performance.</span></span>  
  
- <span data-ttu-id="1bbcf-151">**Konsolidace kódu.**</span><span class="sxs-lookup"><span data-stu-id="1bbcf-151">**Code Consolidation.**</span></span> <span data-ttu-id="1bbcf-152">Kód v obecném typu musí být definován pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-152">The code in a generic type has to be defined only once.</span></span> <span data-ttu-id="1bbcf-153">Sada verzí typu specifických pro typ musí replikovat stejný kód v každé verzi, přičemž jediným rozdílem je konkrétní datový typ pro danou verzi.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-153">A set of type-specific versions of a type must replicate the same code in each version, with the only difference being the specific data type for that version.</span></span> <span data-ttu-id="1bbcf-154">S obecnými typy jsou verze specifické pro typ vygenerovány z původního obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-154">With generic types, the type-specific versions are all generated from the original generic type.</span></span>  
  
- <span data-ttu-id="1bbcf-155">**Opětovné použití kódu.**</span><span class="sxs-lookup"><span data-stu-id="1bbcf-155">**Code Reuse.**</span></span> <span data-ttu-id="1bbcf-156">Kód, který není závislý na konkrétním datovém typu, lze znovu použít s různými datovými typy, pokud je obecný.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-156">Code that does not depend on a particular data type can be reused with various data types if it is generic.</span></span> <span data-ttu-id="1bbcf-157">Můžete ji často použít i s datovým typem, který jste nepůvodně předpovídat.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-157">You can often reuse it even with a data type that you did not originally predict.</span></span>  
  
- <span data-ttu-id="1bbcf-158">**Podpora IDE.**</span><span class="sxs-lookup"><span data-stu-id="1bbcf-158">**IDE Support.**</span></span> <span data-ttu-id="1bbcf-159">Když použijete konstruovaný typ deklarovaný z obecného typu, integrované vývojové prostředí (IDE) vám může poskytnout větší podporu při vývoji kódu.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-159">When you use a constructed type declared from a generic type, the integrated development environment (IDE) can give you more support while you are developing your code.</span></span> <span data-ttu-id="1bbcf-160">Například IntelliSense může zobrazit možnosti specifické pro argument pro konstruktor nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-160">For example, IntelliSense can show you the type-specific options for an argument to a constructor or method.</span></span>  
  
- <span data-ttu-id="1bbcf-161">**Obecné algoritmy**</span><span class="sxs-lookup"><span data-stu-id="1bbcf-161">**Generic Algorithms.**</span></span> <span data-ttu-id="1bbcf-162">Abstraktní algoritmy, které jsou nezávislé na typu, jsou vhodnými kandidáty pro obecné typy.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-162">Abstract algorithms that are type-independent are good candidates for generic types.</span></span> <span data-ttu-id="1bbcf-163">Například obecný postup, který Seřadí položky pomocí rozhraní, <xref:System.IComparable> lze použít s jakýmkoli datovým typem, který implementuje <xref:System.IComparable> .</span><span class="sxs-lookup"><span data-stu-id="1bbcf-163">For example, a generic procedure that sorts items using the <xref:System.IComparable> interface can be used with any data type that implements <xref:System.IComparable>.</span></span>  
  
## <a name="constraints"></a><span data-ttu-id="1bbcf-164">Omezení</span><span class="sxs-lookup"><span data-stu-id="1bbcf-164">Constraints</span></span>  
 <span data-ttu-id="1bbcf-165">I když kód v definici obecného typu by měl být nezávisle na typu, možná budete muset vyžadovat určitou funkci libovolného datového typu, který je součástí vašeho obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-165">Although the code in a generic type definition should be as type-independent as possible, you might need to require a certain capability of any data type supplied to your generic type.</span></span> <span data-ttu-id="1bbcf-166">Například pokud chcete porovnat dvě položky pro účely řazení nebo kompletování, jejich datový typ musí implementovat <xref:System.IComparable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-166">For example, if you want to compare two items for the purpose of sorting or collating, their data type must implement the <xref:System.IComparable> interface.</span></span> <span data-ttu-id="1bbcf-167">Tento požadavek můžete vyhovět přidáním *omezení* do parametru typu.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-167">You can enforce this requirement by adding a *constraint* to the type parameter.</span></span>  
  
### <a name="example-of-a-constraint"></a><span data-ttu-id="1bbcf-168">Příklad omezení</span><span class="sxs-lookup"><span data-stu-id="1bbcf-168">Example of a Constraint</span></span>  
 <span data-ttu-id="1bbcf-169">Následující příklad ukazuje kostru třídy s omezením, které vyžaduje implementaci argumentu typu <xref:System.IComparable> .</span><span class="sxs-lookup"><span data-stu-id="1bbcf-169">The following example shows a skeleton definition of a class with a constraint that requires the type argument to implement <xref:System.IComparable>.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#5)]  
  
 <span data-ttu-id="1bbcf-170">Pokud se další kód pokusí sestavit třídu z `itemManager` zadání typu, který není implementován <xref:System.IComparable> , kompilátor signalizuje chybu.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-170">If subsequent code attempts to construct a class from `itemManager` supplying a type that does not implement <xref:System.IComparable>, the compiler signals an error.</span></span>  
  
### <a name="types-of-constraints"></a><span data-ttu-id="1bbcf-171">Typy omezení</span><span class="sxs-lookup"><span data-stu-id="1bbcf-171">Types of Constraints</span></span>  
 <span data-ttu-id="1bbcf-172">Vaše omezení může v libovolné kombinaci zadat následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="1bbcf-172">Your constraint can specify the following requirements in any combination:</span></span>  
  
- <span data-ttu-id="1bbcf-173">Argument typu musí implementovat jedno nebo víc rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-173">The type argument must implement one or more interfaces</span></span>  
  
- <span data-ttu-id="1bbcf-174">Argument typu musí být typu nebo dědit od, maximálně jedné třídy.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-174">The type argument must be of the type of, or inherit from, at most one class</span></span>  
  
- <span data-ttu-id="1bbcf-175">Argument typu musí zveřejnit konstruktor bez parametrů přístupný kódu, který vytváří objekty z něj.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-175">The type argument must expose a parameterless constructor accessible to the code that creates objects from it</span></span>  
  
- <span data-ttu-id="1bbcf-176">Argument typu musí být *typ odkazu*, nebo musí být *typ hodnoty* .</span><span class="sxs-lookup"><span data-stu-id="1bbcf-176">The type argument must be a *reference type*, or it must be a *value type*</span></span>  
  
 <span data-ttu-id="1bbcf-177">Pokud potřebujete zavést více než jeden požadavek, použijte *seznam omezení* oddělený čárkami uvnitř složených závorek ( `{ }` ).</span><span class="sxs-lookup"><span data-stu-id="1bbcf-177">If you need to impose more than one requirement, you use a comma-separated *constraint list* inside braces (`{ }`).</span></span> <span data-ttu-id="1bbcf-178">Pro vyžadování přístupového konstruktoru zahrnete klíčové slovo [new operátoru](../../../language-reference/operators/new-operator.md) v seznamu.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-178">To require an accessible constructor, you include the [New Operator](../../../language-reference/operators/new-operator.md) keyword in the list.</span></span> <span data-ttu-id="1bbcf-179">Chcete-li vyžadovat typ odkazu, zahrňte `Class` klíčové slovo; pro vyžadování typu hodnoty budete obsahovat `Structure` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-179">To require a reference type, you include the `Class` keyword; to require a value type, you include the `Structure` keyword.</span></span>  
  
 <span data-ttu-id="1bbcf-180">Další informace o omezeních najdete v tématu [seznam typů](../../../language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="1bbcf-180">For more information on constraints, see [Type List](../../../language-reference/statements/type-list.md).</span></span>  
  
### <a name="example-of-multiple-constraints"></a><span data-ttu-id="1bbcf-181">Příklad více omezení</span><span class="sxs-lookup"><span data-stu-id="1bbcf-181">Example of Multiple Constraints</span></span>  
 <span data-ttu-id="1bbcf-182">Následující příklad ukazuje kostru definice obecné třídy se seznamem omezení v parametru typu.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-182">The following example shows a skeleton definition of a generic class with a constraint list on the type parameter.</span></span> <span data-ttu-id="1bbcf-183">V kódu, který vytváří instanci této třídy, musí argument typu implementovat <xref:System.IComparable> <xref:System.IDisposable> rozhraní a, být odkazový typ a vystavit přístupný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-183">In the code that creates an instance of this class, the type argument must implement both the <xref:System.IComparable> and <xref:System.IDisposable> interfaces, be a reference type, and expose an accessible parameterless constructor.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#6)]  
  
## <a name="important-terms"></a><span data-ttu-id="1bbcf-184">Důležité výrazy</span><span class="sxs-lookup"><span data-stu-id="1bbcf-184">Important Terms</span></span>  
 <span data-ttu-id="1bbcf-185">Obecné typy představují a používají následující výrazy:</span><span class="sxs-lookup"><span data-stu-id="1bbcf-185">Generic types introduce and use the following terms:</span></span>  
  
- <span data-ttu-id="1bbcf-186">*Obecný typ*</span><span class="sxs-lookup"><span data-stu-id="1bbcf-186">*Generic Type*.</span></span> <span data-ttu-id="1bbcf-187">Definice třídy, struktury, rozhraní, procedury nebo delegáta, pro který zadáte alespoň jeden datový typ při jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-187">A definition of a class, structure, interface, procedure, or delegate for which you supply at least one data type when you declare it.</span></span>  
  
- <span data-ttu-id="1bbcf-188">*Parametr typu*</span><span class="sxs-lookup"><span data-stu-id="1bbcf-188">*Type Parameter*.</span></span> <span data-ttu-id="1bbcf-189">V definici obecného typu je zástupný symbol pro datový typ, který zadáte při deklaraci typu.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-189">In a generic type definition, a placeholder for a data type you supply when you declare the type.</span></span>  
  
- <span data-ttu-id="1bbcf-190">*Argument typu*</span><span class="sxs-lookup"><span data-stu-id="1bbcf-190">*Type Argument*.</span></span> <span data-ttu-id="1bbcf-191">Konkrétní datový typ, který nahradí parametr typu při deklaraci vytvořeného typu z obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-191">A specific data type that replaces a type parameter when you declare a constructed type from a generic type.</span></span>  
  
- <span data-ttu-id="1bbcf-192">*Omezení*.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-192">*Constraint*.</span></span> <span data-ttu-id="1bbcf-193">Podmínka u parametru typu, který omezuje argument typu, který můžete pro něj zadat.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-193">A condition on a type parameter that restricts the type argument you can supply for it.</span></span> <span data-ttu-id="1bbcf-194">Omezení může vyžadovat, aby argument typu vyžadoval implementaci konkrétního rozhraní, nebo dědění z konkrétní třídy, mít přístupný konstruktor bez parametrů, nebo jako typ odkazu nebo typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-194">A constraint can require that the type argument must implement a particular interface, be or inherit from a particular class, have an accessible parameterless constructor, or be a reference type or a value type.</span></span> <span data-ttu-id="1bbcf-195">Tato omezení můžete kombinovat, ale můžete zadat maximálně jednu třídu.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-195">You can combine these constraints, but you can specify at most one class.</span></span>  
  
- <span data-ttu-id="1bbcf-196">*Konstruovaný typ*.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-196">*Constructed Type*.</span></span> <span data-ttu-id="1bbcf-197">Třída, struktura, rozhraní, procedura nebo delegát deklarované z obecného typu zadáním argumentů typu pro jeho parametry typu.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-197">A class, structure, interface, procedure, or delegate declared from a generic type by supplying type arguments for its type parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bbcf-198">Viz také</span><span class="sxs-lookup"><span data-stu-id="1bbcf-198">See also</span></span>

- [<span data-ttu-id="1bbcf-199">Datové typy</span><span class="sxs-lookup"><span data-stu-id="1bbcf-199">Data Types</span></span>](index.md)
- [<span data-ttu-id="1bbcf-200">Znaky typu</span><span class="sxs-lookup"><span data-stu-id="1bbcf-200">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="1bbcf-201">Typy hodnot a typy odkazu</span><span class="sxs-lookup"><span data-stu-id="1bbcf-201">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="1bbcf-202">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1bbcf-202">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="1bbcf-203">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="1bbcf-203">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="1bbcf-204">Datové typy</span><span class="sxs-lookup"><span data-stu-id="1bbcf-204">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="1bbcf-205">Tohoto</span><span class="sxs-lookup"><span data-stu-id="1bbcf-205">Of</span></span>](../../../language-reference/statements/of-clause.md)
- [<span data-ttu-id="1bbcf-206">Formátu</span><span class="sxs-lookup"><span data-stu-id="1bbcf-206">As</span></span>](../../../language-reference/statements/as-clause.md)
- [<span data-ttu-id="1bbcf-207">Datový typ objektu</span><span class="sxs-lookup"><span data-stu-id="1bbcf-207">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="1bbcf-208">Kovariance a kontravariance</span><span class="sxs-lookup"><span data-stu-id="1bbcf-208">Covariance and Contravariance</span></span>](../../concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="1bbcf-209">Iterátory</span><span class="sxs-lookup"><span data-stu-id="1bbcf-209">Iterators</span></span>](../../concepts/iterators.md)
