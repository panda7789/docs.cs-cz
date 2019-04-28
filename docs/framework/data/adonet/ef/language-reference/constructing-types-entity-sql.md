---
title: Vytváření typů (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 53aa7fcc82a476c8b8bd87b059e08bee6741c0d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61605832"
---
# <a name="constructing-types-entity-sql"></a><span data-ttu-id="01fde-102">Vytváření typů (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="01fde-102">Constructing Types (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="01fde-103">nabízí tři druhy konstruktory: řádek konstruktory, konstruktory s názvem typu a kolekce konstruktory.</span><span class="sxs-lookup"><span data-stu-id="01fde-103">provides three kinds of constructors: row constructors, named type constructors, and collection constructors.</span></span>  
  
## <a name="row-constructors"></a><span data-ttu-id="01fde-104">Řádek konstruktory</span><span class="sxs-lookup"><span data-stu-id="01fde-104">Row Constructors</span></span>  
 <span data-ttu-id="01fde-105">Použití konstruktorů řádek v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] k sestavení kompletních anonymní, strukturálně typy záznamů z jedné nebo více hodnot.</span><span class="sxs-lookup"><span data-stu-id="01fde-105">You use row constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="01fde-106">Výsledný typ konstruktoru řádku je typ řádku, jejichž pole typy odpovídají typům hodnot použitých k vytvoření řádku.</span><span class="sxs-lookup"><span data-stu-id="01fde-106">The result type of a row constructor is a row type whose field types correspond to the types of the values used to construct the row.</span></span> <span data-ttu-id="01fde-107">Například následující výraz vytvoří hodnotu typu `Record(a int, b string, c int)`:</span><span class="sxs-lookup"><span data-stu-id="01fde-107">For example, the following expression constructs a value of type `Record(a int, b string, c int)`:</span></span>  
  
 `ROW(1 AS a, "abc" AS b, a + 34 AS c)`  
  
 <span data-ttu-id="01fde-108">Pokud nezadáte alias pro výraz v konstruktoru row, Entity Framework se pokusí vygenerovat.</span><span class="sxs-lookup"><span data-stu-id="01fde-108">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="01fde-109">Další informace najdete v části "Pravidla pro aliasy" v [identifikátory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="01fde-109">For more information, see the "Aliasing Rules" section in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="01fde-110">Výraz aliasing v konstruktoru row platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="01fde-110">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
- <span data-ttu-id="01fde-111">Výrazy v konstruktoru row nelze odkazovat na jiné aliasy v konstruktoru stejné.</span><span class="sxs-lookup"><span data-stu-id="01fde-111">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
- <span data-ttu-id="01fde-112">Dvou výrazů ve stejné konstruktor row nemůže mít stejný alias.</span><span class="sxs-lookup"><span data-stu-id="01fde-112">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="01fde-113">Další informace o konstruktorech řádku, naleznete v tématu [řádek](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="01fde-113">For more information about row constructors, see [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span></span>  
  
## <a name="collection-constructors"></a><span data-ttu-id="01fde-114">Kolekce konstruktory</span><span class="sxs-lookup"><span data-stu-id="01fde-114">Collection Constructors</span></span>  
 <span data-ttu-id="01fde-115">Použití konstruktorů kolekce v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] k vytvoření instance multisady ze seznamu hodnot.</span><span class="sxs-lookup"><span data-stu-id="01fde-115">You use collection constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="01fde-116">Všechny hodnoty v konstruktoru musí být typu vzájemně kompatibilní `T`, a konstruktor vytvoří kolekci typu `Multiset<T>`.</span><span class="sxs-lookup"><span data-stu-id="01fde-116">All the values in the constructor must be of mutually compatible type `T`, and the constructor produces a collection of type `Multiset<T>`.</span></span> <span data-ttu-id="01fde-117">Například následující výraz vytvoří kolekci celých čísel:</span><span class="sxs-lookup"><span data-stu-id="01fde-117">For example, the following expression creates a collection of integers:</span></span>  
  
 `Multiset(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
 <span data-ttu-id="01fde-118">Multiset – prázdný konstruktory nejsou povolené, protože nelze určit typ elementů.</span><span class="sxs-lookup"><span data-stu-id="01fde-118">Empty multiset constructors are not allowed because the type of the elements cannot be determined.</span></span> <span data-ttu-id="01fde-119">Toto není platná:</span><span class="sxs-lookup"><span data-stu-id="01fde-119">The following is not valid:</span></span>  
  
 `multiset() {}`  
  
 <span data-ttu-id="01fde-120">Další informace najdete v tématu [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="01fde-120">For more information, see [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md).</span></span>  
  
## <a name="named-type-constructors-namedtype-initializers"></a><span data-ttu-id="01fde-121">Konstruktory (NamedType inicializátory) s názvem typu</span><span class="sxs-lookup"><span data-stu-id="01fde-121">Named Type Constructors (NamedType Initializers)</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="01fde-122">Umožňuje konstruktory typu (inicializátory) k vytvoření instance s názvem komplexní typy a typy entit.</span><span class="sxs-lookup"><span data-stu-id="01fde-122">allows type constructors (initializers) to create instances of named complex types and entity types.</span></span> <span data-ttu-id="01fde-123">Například následující výraz vytvoří instanci `Person` typu.</span><span class="sxs-lookup"><span data-stu-id="01fde-123">For example, the following expression creates an instance of a `Person` type.</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="01fde-124">Následující výraz vytvoří instanci komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="01fde-124">The following expression creates an instance of a complex type.</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="01fde-125">Následující výraz vytvoří instanci vnořené komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="01fde-125">The following expression creates an instance of a nested complex type.</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="01fde-126">Následující výraz vytvoří instanci entity vnořené komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="01fde-126">The following expression creates an instance of an entity with a nested complex type.</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="01fde-127">Následující příklad ukazuje způsob inicializace vlastností komplexního typu na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="01fde-127">The following example shows how to initialize a property of a complex type to null.</span></span> `MyModel.ZipCode(‘98118’, null)`  
  
 <span data-ttu-id="01fde-128">Argumenty pro konstruktor předpokládá, že jsou ve stejném pořadí jako deklarace atributy typu.</span><span class="sxs-lookup"><span data-stu-id="01fde-128">The arguments to the constructor are assumed to be in the same order as the declaration of the attributes of the type.</span></span>  
  
 <span data-ttu-id="01fde-129">Další informace najdete v tématu [konstruktor typu s názvem](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="01fde-129">For more information, see [Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01fde-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01fde-130">See also</span></span>

- [<span data-ttu-id="01fde-131">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="01fde-131">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="01fde-132">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="01fde-132">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="01fde-133">Systém typů</span><span class="sxs-lookup"><span data-stu-id="01fde-133">Type System</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)
