---
title: 'Inicializátory objektů: pojmenované a anonymní typy'
ms.date: 07/20/2015
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
ms.openlocfilehash: e6ffc649d7eb841c2d009b0ec1237975f46e2d2d
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636806"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a><span data-ttu-id="273af-102">Inicializátory objektů: pojmenované a anonymní typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="273af-102">Object Initializers: Named and Anonymous Types (Visual Basic)</span></span>
<span data-ttu-id="273af-103">Inicializátory objektů umožňují určit vlastnosti složitého objektu pomocí jediného výrazu.</span><span class="sxs-lookup"><span data-stu-id="273af-103">Object initializers enable you to specify properties for a complex object by using a single expression.</span></span> <span data-ttu-id="273af-104">Lze je použít k vytvoření instancí pojmenovaných typů a anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="273af-104">They can be used to create instances of named types and of anonymous types.</span></span>  
  
## <a name="declarations"></a><span data-ttu-id="273af-105">Deklarace</span><span class="sxs-lookup"><span data-stu-id="273af-105">Declarations</span></span>  
 <span data-ttu-id="273af-106">Deklarace instancí pojmenovaných a anonymních typů mohou vypadat téměř stejně, ale jejich účinky nejsou stejné.</span><span class="sxs-lookup"><span data-stu-id="273af-106">Declarations of instances of named and anonymous types can look almost identical, but their effects are not the same.</span></span> <span data-ttu-id="273af-107">Každá kategorie má možnosti a omezení vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="273af-107">Each category has abilities and restrictions of its own.</span></span> <span data-ttu-id="273af-108">Následující příklad ukazuje pohodlný způsob, jak deklarovat a inicializovat instanci pojmenované třídy, `Customer`, pomocí seznamu inicializátorů objektů.</span><span class="sxs-lookup"><span data-stu-id="273af-108">The following example shows a convenient way to declare and initialize an instance of a named class, `Customer`, by using an object initializer list.</span></span> <span data-ttu-id="273af-109">Všimněte si, že název třídy je zadán za klíčovým slovem `New`.</span><span class="sxs-lookup"><span data-stu-id="273af-109">Notice that the name of the class is specified after the keyword `New`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 <span data-ttu-id="273af-110">Anonymní typ nemá žádný použitelný název.</span><span class="sxs-lookup"><span data-stu-id="273af-110">An anonymous type has no usable name.</span></span> <span data-ttu-id="273af-111">Proto vytváření instancí anonymního typu nemůže obsahovat název třídy.</span><span class="sxs-lookup"><span data-stu-id="273af-111">Therefore an instantiation of an anonymous type cannot include a class name.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 <span data-ttu-id="273af-112">Požadavky a výsledky těchto dvou deklarací nejsou stejné.</span><span class="sxs-lookup"><span data-stu-id="273af-112">The requirements and results of the two declarations are not the same.</span></span> <span data-ttu-id="273af-113">Pro `namedCust`musí již existovat `Customer` třída, která má vlastnost `Name`, a deklarace vytvoří instanci této třídy.</span><span class="sxs-lookup"><span data-stu-id="273af-113">For `namedCust`, a `Customer` class that has a `Name` property must already exist, and the declaration creates an instance of that class.</span></span> <span data-ttu-id="273af-114">Pro `anonymousCust`kompilátor definuje novou třídu, která má jednu vlastnost, řetězec nazvaný `Name`a vytvoří novou instanci této třídy.</span><span class="sxs-lookup"><span data-stu-id="273af-114">For `anonymousCust`, the compiler defines a new class that has one property, a string called `Name`, and creates a new instance of that class.</span></span>  
  
## <a name="named-types"></a><span data-ttu-id="273af-115">Pojmenované typy</span><span class="sxs-lookup"><span data-stu-id="273af-115">Named Types</span></span>  
 <span data-ttu-id="273af-116">Inicializátory objektů poskytují jednoduchý způsob volání konstruktoru typu a poté nastavení hodnot některých nebo všech vlastností v jednom příkazu.</span><span class="sxs-lookup"><span data-stu-id="273af-116">Object initializers provide a simple way to call the constructor of a type and then set the values of some or all properties in a single statement.</span></span> <span data-ttu-id="273af-117">Kompilátor vyvolá příslušný konstruktor pro příkaz: konstruktor bez parametrů, pokud nejsou zadány žádné argumenty, nebo parametrizovaný konstruktor při odeslání jednoho nebo více argumentů.</span><span class="sxs-lookup"><span data-stu-id="273af-117">The compiler invokes the appropriate constructor for the statement: the parameterless constructor if no arguments are presented, or a parameterized constructor if one or more arguments are sent.</span></span> <span data-ttu-id="273af-118">Poté jsou zadané vlastnosti inicializovány v pořadí, ve kterém jsou uvedeny v seznamu inicializátorů.</span><span class="sxs-lookup"><span data-stu-id="273af-118">After that, the specified properties are initialized in the order in which they are presented in the initializer list.</span></span>  
  
 <span data-ttu-id="273af-119">Každá inicializace v seznamu inicializátorů se skládá z přiřazení počáteční hodnoty ke členu třídy.</span><span class="sxs-lookup"><span data-stu-id="273af-119">Each initialization in the initializer list consists of the assignment of an initial value to a member of the class.</span></span> <span data-ttu-id="273af-120">Názvy a datové typy členů jsou určeny při definování třídy.</span><span class="sxs-lookup"><span data-stu-id="273af-120">The names and data types of the members are determined when the class is defined.</span></span> <span data-ttu-id="273af-121">V následujících příkladech musí třída `Customer` existovat a musí mít členy s názvem `Name` a `City`, které mohou přijímat řetězcové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="273af-121">In the following examples, the `Customer` class must exist, and must have members named `Name` and `City` that can accept string values.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 <span data-ttu-id="273af-122">Alternativně můžete získat stejný výsledek pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="273af-122">Alternatively, you can obtain the same result by using the following code:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 <span data-ttu-id="273af-123">Každá z těchto deklarací je ekvivalentní následujícímu příkladu, který vytvoří objekt `Customer` pomocí konstruktoru bez parametrů a pak určí počáteční hodnoty vlastností `Name` a `City` pomocí příkazu `With`.</span><span class="sxs-lookup"><span data-stu-id="273af-123">Each of these declarations is equivalent to the following example, which creates a `Customer` object by using the parameterless constructor, and then specifies initial values for the `Name` and `City` properties by using a `With` statement.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 <span data-ttu-id="273af-124">Pokud třída `Customer` obsahuje parametrizovaný konstruktor, který umožňuje odeslat hodnotu pro `Name`, například, můžete deklarovat a inicializovat objekt `Customer` následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="273af-124">If the `Customer` class contains a parameterized constructor that enables you to send in a value for `Name`, for example, you can also declare and initialize a `Customer` object in the following ways:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 <span data-ttu-id="273af-125">Nemusíte inicializovat všechny vlastnosti, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="273af-125">You do not have to initialize all properties, as the following code shows.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 <span data-ttu-id="273af-126">Inicializační seznam ale nemůže být prázdný.</span><span class="sxs-lookup"><span data-stu-id="273af-126">However, the initialization list cannot be empty.</span></span> <span data-ttu-id="273af-127">Neinicializované vlastnosti uchovávají jejich výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="273af-127">Uninitialized properties retain their default values.</span></span>  
  
### <a name="type-inference-with-named-types"></a><span data-ttu-id="273af-128">Odvození typu s pojmenovanými typy</span><span class="sxs-lookup"><span data-stu-id="273af-128">Type Inference with Named Types</span></span>  
 <span data-ttu-id="273af-129">Můžete zkrátit kód pro deklaraci `cust1` kombinováním inicializátorů objektů a odvození místního typu.</span><span class="sxs-lookup"><span data-stu-id="273af-129">You can shorten the code for the declaration of `cust1` by combining object initializers and local type inference.</span></span> <span data-ttu-id="273af-130">To umožňuje vynechat klauzuli `As` v deklaraci proměnné.</span><span class="sxs-lookup"><span data-stu-id="273af-130">This enables you to omit the `As` clause in the variable declaration.</span></span> <span data-ttu-id="273af-131">Datový typ proměnné je odvozen z typu objektu, který je vytvořen přiřazením.</span><span class="sxs-lookup"><span data-stu-id="273af-131">The data type of the variable is inferred from the type of the object that is created by the assignment.</span></span> <span data-ttu-id="273af-132">V následujícím příkladu je typ `cust6` `Customer`.</span><span class="sxs-lookup"><span data-stu-id="273af-132">In the following example, the type of `cust6` is `Customer`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a><span data-ttu-id="273af-133">Poznámky k pojmenovaným typům</span><span class="sxs-lookup"><span data-stu-id="273af-133">Remarks About Named Types</span></span>  
  
- <span data-ttu-id="273af-134">Člen třídy nelze v seznamu inicializátoru objektu inicializovat více než jednou.</span><span class="sxs-lookup"><span data-stu-id="273af-134">A class member cannot be initialized more than one time in the object initializer list.</span></span> <span data-ttu-id="273af-135">Deklarace `cust7` způsobí chybu.</span><span class="sxs-lookup"><span data-stu-id="273af-135">The declaration of `cust7` causes an error.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
- <span data-ttu-id="273af-136">Člen lze použít k inicializaci samotného nebo jiného pole.</span><span class="sxs-lookup"><span data-stu-id="273af-136">A member can be used to initialize itself or another field.</span></span> <span data-ttu-id="273af-137">Pokud je před inicializací členem otevřen, jako v následující deklaraci pro `cust8`, bude použita výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="273af-137">If a member is accessed before it has been initialized, as in the following declaration for `cust8`, the default value will be used.</span></span> <span data-ttu-id="273af-138">Pamatujte, že pokud je zpracována deklarace, která používá inicializátor objektu, první věc, ke které dojde, je vyvolán příslušný konstruktor.</span><span class="sxs-lookup"><span data-stu-id="273af-138">Remember that when a declaration that uses an object initializer is processed, the first thing that happens is that the appropriate constructor is invoked.</span></span> <span data-ttu-id="273af-139">Poté jsou inicializována jednotlivá pole v seznamu inicializátorů.</span><span class="sxs-lookup"><span data-stu-id="273af-139">After that, the individual fields in the initializer list are initialized.</span></span> <span data-ttu-id="273af-140">V následujících příkladech je výchozí hodnota pro `Name` přiřazena `cust8`a inicializovaná hodnota je přiřazena v `cust9`.</span><span class="sxs-lookup"><span data-stu-id="273af-140">In the following examples, the default value for `Name` is assigned for `cust8`, and an initialized value is assigned in `cust9`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     <span data-ttu-id="273af-141">Následující příklad používá parametrizovaný konstruktor z `cust3` a `cust4` k deklaraci a inicializaci `cust10` a `cust11`.</span><span class="sxs-lookup"><span data-stu-id="273af-141">The following example uses the parameterized constructor from `cust3` and `cust4` to declare and initialize `cust10` and `cust11`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
- <span data-ttu-id="273af-142">Inicializátory objektů můžou být vnořené.</span><span class="sxs-lookup"><span data-stu-id="273af-142">Object initializers can be nested.</span></span> <span data-ttu-id="273af-143">V následujícím příkladu je `AddressClass` třída, která má dvě vlastnosti, `City` a `State`a třída `Customer` má `Address` vlastnost, která je instancí `AddressClass`.</span><span class="sxs-lookup"><span data-stu-id="273af-143">In the following example, `AddressClass` is a class that has two properties, `City` and `State`, and the `Customer` class has an `Address` property that is an instance of `AddressClass`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
- <span data-ttu-id="273af-144">Seznam inicializace nemůže být prázdný.</span><span class="sxs-lookup"><span data-stu-id="273af-144">The initialization list cannot be empty.</span></span>  
  
- <span data-ttu-id="273af-145">Inicializovaná instance nemůže být typu Object.</span><span class="sxs-lookup"><span data-stu-id="273af-145">The instance being initialized cannot be of type Object.</span></span>  
  
- <span data-ttu-id="273af-146">Členy třídy, které jsou inicializovány, nemohou být sdíleny členy, členy jen pro čtení, konstanty nebo volání metod.</span><span class="sxs-lookup"><span data-stu-id="273af-146">Class members being initialized cannot be shared members, read-only members, constants, or method calls.</span></span>  
  
- <span data-ttu-id="273af-147">Inicializace členů třídy nemůže být indexována ani kvalifikována.</span><span class="sxs-lookup"><span data-stu-id="273af-147">Class members being initialized cannot be indexed or qualified.</span></span> <span data-ttu-id="273af-148">Následující příklady vyvolávají chyby kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="273af-148">The following examples raise compiler errors:</span></span>  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a><span data-ttu-id="273af-149">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="273af-149">Anonymous Types</span></span>  
 <span data-ttu-id="273af-150">Anonymní typy používají Inicializátory objektů k vytváření instancí nových typů, které nemusíte explicitně definovat a pojmenovat.</span><span class="sxs-lookup"><span data-stu-id="273af-150">Anonymous types use object initializers to create instances of new types that you do not explicitly define and name.</span></span> <span data-ttu-id="273af-151">Místo toho kompilátor vygeneruje typ podle vlastností, které určíte v seznamu inicializátorů objektů.</span><span class="sxs-lookup"><span data-stu-id="273af-151">Instead, the compiler generates a type according to the properties you designate in the object initializer list.</span></span> <span data-ttu-id="273af-152">Vzhledem k tomu, že název typu není zadán, je označován jako *anonymní typ*.</span><span class="sxs-lookup"><span data-stu-id="273af-152">Because the name of the type is not specified, it is referred to as an *anonymous type*.</span></span> <span data-ttu-id="273af-153">Například Porovnejte následující deklaraci se staršími verzemi pro `cust6`.</span><span class="sxs-lookup"><span data-stu-id="273af-153">For example, compare the following declaration to the earlier one for `cust6`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 <span data-ttu-id="273af-154">Jediný rozdíl syntakticky znamená, že po `New` pro datový typ není zadán žádný název.</span><span class="sxs-lookup"><span data-stu-id="273af-154">The only difference syntactically is that no name is specified after `New` for the data type.</span></span> <span data-ttu-id="273af-155">K čemu ale dojde poměrně jinak.</span><span class="sxs-lookup"><span data-stu-id="273af-155">However, what happens is quite different.</span></span> <span data-ttu-id="273af-156">Kompilátor definuje nový anonymní typ, který má dvě vlastnosti, `Name` a `City`a vytvoří instanci objektu s určenými hodnotami.</span><span class="sxs-lookup"><span data-stu-id="273af-156">The compiler defines a new anonymous type that has two properties, `Name` and `City`, and creates an instance of it with the specified values.</span></span> <span data-ttu-id="273af-157">Odvození typu Určuje typy `Name` a `City` v příkladu jako řetězce.</span><span class="sxs-lookup"><span data-stu-id="273af-157">Type inference determines the types of `Name` and `City` in the example to be strings.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="273af-158">Název anonymního typu je generován kompilátorem a může se lišit od kompilace po kompilaci.</span><span class="sxs-lookup"><span data-stu-id="273af-158">The name of the anonymous type is generated by the compiler, and may vary from compilation to compilation.</span></span> <span data-ttu-id="273af-159">Váš kód by neměl používat nebo spoléhat na název anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="273af-159">Your code should not use or rely on the name of an anonymous type.</span></span>  
  
 <span data-ttu-id="273af-160">Vzhledem k tomu, že název typu není k dispozici, nelze použít klauzuli `As` k deklaraci `cust13`.</span><span class="sxs-lookup"><span data-stu-id="273af-160">Because the name of the type is not available, you cannot use an `As` clause to declare `cust13`.</span></span> <span data-ttu-id="273af-161">Jeho typ musí být odvozený.</span><span class="sxs-lookup"><span data-stu-id="273af-161">Its type must be inferred.</span></span> <span data-ttu-id="273af-162">Bez použití pozdní vazby omezuje použití anonymních typů na lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="273af-162">Without using late binding, this limits the use of anonymous types to local variables.</span></span>  
  
 <span data-ttu-id="273af-163">Anonymní typy poskytují kritickou podporu pro dotazy LINQ.</span><span class="sxs-lookup"><span data-stu-id="273af-163">Anonymous types provide critical support for LINQ queries.</span></span> <span data-ttu-id="273af-164">Další informace o použití anonymních typů v dotazech naleznete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) a [Úvod do LINQ v Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).</span><span class="sxs-lookup"><span data-stu-id="273af-164">For more information about the use of anonymous types in queries, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) and [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).</span></span>  
  
### <a name="remarks-about-anonymous-types"></a><span data-ttu-id="273af-165">Poznámky k anonymním typům</span><span class="sxs-lookup"><span data-stu-id="273af-165">Remarks About Anonymous Types</span></span>  
  
- <span data-ttu-id="273af-166">Obvykle všechny nebo většina vlastností v deklaraci anonymního typu budou mít klíčové vlastnosti, které jsou označeny zadáním klíčového slova `Key` před názvem vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="273af-166">Typically, all or most of the properties in an anonymous type declaration will be key properties, which are indicated by typing the keyword `Key` in front of the property name.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     <span data-ttu-id="273af-167">Další informace o vlastnostech klíče najdete v tématu [Key](../../../../visual-basic/language-reference/modifiers/key.md).</span><span class="sxs-lookup"><span data-stu-id="273af-167">For more information about key properties, see [Key](../../../../visual-basic/language-reference/modifiers/key.md).</span></span>  
  
- <span data-ttu-id="273af-168">Podobně jako pojmenované typy, inicializační seznamy pro definice anonymního typu musí deklarovat alespoň jednu vlastnost.</span><span class="sxs-lookup"><span data-stu-id="273af-168">Like named types, initializer lists for anonymous type definitions must declare at least one property.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
- <span data-ttu-id="273af-169">Je-li deklarována instance anonymního typu, kompilátor vygeneruje vyhovující definici anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="273af-169">When an instance of an anonymous type is declared, the compiler generates a matching anonymous type definition.</span></span> <span data-ttu-id="273af-170">Názvy a datové typy vlastností jsou odebírány z deklarace instance a jsou součástí kompilátoru v definici.</span><span class="sxs-lookup"><span data-stu-id="273af-170">The names and data types of the properties are taken from the instance declaration, and are included by the compiler in the definition.</span></span> <span data-ttu-id="273af-171">Vlastnosti nejsou pojmenované a jsou definovány předem, protože by byly pro pojmenovaný typ.</span><span class="sxs-lookup"><span data-stu-id="273af-171">The properties are not named and defined in advance, as they would be for a named type.</span></span> <span data-ttu-id="273af-172">Jejich typy jsou odvozeny.</span><span class="sxs-lookup"><span data-stu-id="273af-172">Their types are inferred.</span></span> <span data-ttu-id="273af-173">Pomocí klauzule `As` nemůžete zadat datové typy vlastností.</span><span class="sxs-lookup"><span data-stu-id="273af-173">You cannot specify the data types of the properties by using an `As` clause.</span></span>  
  
- <span data-ttu-id="273af-174">Anonymní typy mohou také vytvořit názvy a hodnoty jejich vlastností několika různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="273af-174">Anonymous types can also establish the names and values of their properties in several other ways.</span></span> <span data-ttu-id="273af-175">Například vlastnost anonymního typu může převzít název i hodnotu proměnné nebo název a hodnotu vlastnosti jiného objektu.</span><span class="sxs-lookup"><span data-stu-id="273af-175">For example, an anonymous type property can take both the name and the value of a variable, or the name and value of a property of another object.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     <span data-ttu-id="273af-176">Další informace o možnostech definování vlastností v anonymních typech naleznete v tématu [How to: odvozování názvů a typů vlastností v deklaracích anonymního typu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span><span class="sxs-lookup"><span data-stu-id="273af-176">For more information about the options for defining properties in anonymous types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="273af-177">Viz také:</span><span class="sxs-lookup"><span data-stu-id="273af-177">See also</span></span>

- [<span data-ttu-id="273af-178">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="273af-178">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="273af-179">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="273af-179">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="273af-180">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="273af-180">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="273af-181">Postupy: Odvození názvů a typů vlastností v deklaracích anonymního typu</span><span class="sxs-lookup"><span data-stu-id="273af-181">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="273af-182">Key</span><span class="sxs-lookup"><span data-stu-id="273af-182">Key</span></span>](../../../../visual-basic/language-reference/modifiers/key.md)
- [<span data-ttu-id="273af-183">Postupy: Deklarace objektu pomocí inicializátoru objektu</span><span class="sxs-lookup"><span data-stu-id="273af-183">How to: Declare an Object by Using an Object Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
