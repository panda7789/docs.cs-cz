---
title: Vytváření typů (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 7113aaf1c2caa982a8ab4751928856c1271570cb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251123"
---
# <a name="constructing-types-entity-sql"></a><span data-ttu-id="5d67a-102">Vytváření typů (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5d67a-102">Constructing Types (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="5d67a-103">poskytuje tři druhy konstruktorů: konstruktory řádků, pojmenované typové konstruktory a konstruktory kolekcí.</span><span class="sxs-lookup"><span data-stu-id="5d67a-103">provides three kinds of constructors: row constructors, named type constructors, and collection constructors.</span></span>  
  
## <a name="row-constructors"></a><span data-ttu-id="5d67a-104">Konstruktory řádků</span><span class="sxs-lookup"><span data-stu-id="5d67a-104">Row Constructors</span></span>  
 <span data-ttu-id="5d67a-105">Konstruktory řádků v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nástroji slouží k vytváření anonymních strukturovaných typů záznamů z jedné nebo více hodnot.</span><span class="sxs-lookup"><span data-stu-id="5d67a-105">You use row constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="5d67a-106">Typ výsledku konstruktoru řádku je typ řádku, jehož typy polí odpovídají typům hodnot, které slouží k vytvoření řádku.</span><span class="sxs-lookup"><span data-stu-id="5d67a-106">The result type of a row constructor is a row type whose field types correspond to the types of the values used to construct the row.</span></span> <span data-ttu-id="5d67a-107">Například následující výraz vytvoří hodnotu typu `Record(a int, b string, c int)`:</span><span class="sxs-lookup"><span data-stu-id="5d67a-107">For example, the following expression constructs a value of type `Record(a int, b string, c int)`:</span></span>  
  
 `ROW(1 AS a, "abc" AS b, a + 34 AS c)`  
  
 <span data-ttu-id="5d67a-108">Pokud neposkytnete alias pro výraz v konstruktoru řádku, Entity Framework se pokusí jednu vygenerovat.</span><span class="sxs-lookup"><span data-stu-id="5d67a-108">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="5d67a-109">Další informace najdete v části pravidla aliasing v tématu [identifikátory](identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5d67a-109">For more information, see the "Aliasing Rules" section in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="5d67a-110">Následující pravidla platí pro aliasy výrazů v konstruktoru řádku:</span><span class="sxs-lookup"><span data-stu-id="5d67a-110">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
- <span data-ttu-id="5d67a-111">Výrazy v konstruktoru řádku nemůžou odkazovat na jiné aliasy ve stejném konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="5d67a-111">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
- <span data-ttu-id="5d67a-112">Dva výrazy v konstruktoru stejného řádku nemohou mít stejný alias.</span><span class="sxs-lookup"><span data-stu-id="5d67a-112">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="5d67a-113">Další informace o konstruktorech řádků naleznete v tématu [řádek](row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5d67a-113">For more information about row constructors, see [ROW](row-entity-sql.md).</span></span>  
  
## <a name="collection-constructors"></a><span data-ttu-id="5d67a-114">Konstruktory kolekcí</span><span class="sxs-lookup"><span data-stu-id="5d67a-114">Collection Constructors</span></span>  
 <span data-ttu-id="5d67a-115">Konstruktory kolekce v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nástroji slouží k vytvoření instance multiset ze seznamu hodnot.</span><span class="sxs-lookup"><span data-stu-id="5d67a-115">You use collection constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="5d67a-116">Všechny hodnoty v konstruktoru musí být vzájemně kompatibilního typu `T`a konstruktor vytvoří kolekci typu. `Multiset<T>`</span><span class="sxs-lookup"><span data-stu-id="5d67a-116">All the values in the constructor must be of mutually compatible type `T`, and the constructor produces a collection of type `Multiset<T>`.</span></span> <span data-ttu-id="5d67a-117">Například následující výraz vytvoří kolekci celých čísel:</span><span class="sxs-lookup"><span data-stu-id="5d67a-117">For example, the following expression creates a collection of integers:</span></span>  
  
 `Multiset(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
 <span data-ttu-id="5d67a-118">Prázdné konstruktory multiset nejsou povoleny, protože nelze určit typ elementů.</span><span class="sxs-lookup"><span data-stu-id="5d67a-118">Empty multiset constructors are not allowed because the type of the elements cannot be determined.</span></span> <span data-ttu-id="5d67a-119">Následující není platný:</span><span class="sxs-lookup"><span data-stu-id="5d67a-119">The following is not valid:</span></span>  
  
 `multiset() {}`  
  
 <span data-ttu-id="5d67a-120">Další informace najdete v tématu [MULTISET](multiset-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5d67a-120">For more information, see [MULTISET](multiset-entity-sql.md).</span></span>  
  
## <a name="named-type-constructors-namedtype-initializers"></a><span data-ttu-id="5d67a-121">Konstruktory pojmenovaného typu (Inicializátory NamedType)</span><span class="sxs-lookup"><span data-stu-id="5d67a-121">Named Type Constructors (NamedType Initializers)</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="5d67a-122">povoluje konstruktory typů (Inicializátory) k vytváření instancí pojmenovaných komplexních typů a typů entit.</span><span class="sxs-lookup"><span data-stu-id="5d67a-122">allows type constructors (initializers) to create instances of named complex types and entity types.</span></span> <span data-ttu-id="5d67a-123">Například následující výraz vytvoří instanci `Person` typu.</span><span class="sxs-lookup"><span data-stu-id="5d67a-123">For example, the following expression creates an instance of a `Person` type.</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="5d67a-124">Následující výraz vytvoří instanci komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="5d67a-124">The following expression creates an instance of a complex type.</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="5d67a-125">Následující výraz vytvoří instanci vnořeného komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="5d67a-125">The following expression creates an instance of a nested complex type.</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="5d67a-126">Následující výraz vytvoří instanci entity s vnořeným komplexním typem.</span><span class="sxs-lookup"><span data-stu-id="5d67a-126">The following expression creates an instance of an entity with a nested complex type.</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="5d67a-127">Následující příklad ukazuje, jak inicializovat vlastnost komplexního typu na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="5d67a-127">The following example shows how to initialize a property of a complex type to null.</span></span> `MyModel.ZipCode(‘98118’, null)`  
  
 <span data-ttu-id="5d67a-128">Předpokládá se, že argumenty konstruktoru jsou ve stejném pořadí jako deklarace atributů typu.</span><span class="sxs-lookup"><span data-stu-id="5d67a-128">The arguments to the constructor are assumed to be in the same order as the declaration of the attributes of the type.</span></span>  
  
 <span data-ttu-id="5d67a-129">Další informace naleznete v tématu [konstruktor pojmenovaného typu](named-type-constructor-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5d67a-129">For more information, see [Named Type Constructor](named-type-constructor-entity-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d67a-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d67a-130">See also</span></span>

- [<span data-ttu-id="5d67a-131">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5d67a-131">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="5d67a-132">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5d67a-132">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="5d67a-133">Systém typů</span><span class="sxs-lookup"><span data-stu-id="5d67a-133">Type System</span></span>](type-system-entity-sql.md)
