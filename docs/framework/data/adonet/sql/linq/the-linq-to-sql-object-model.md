---
title: Technologie LINQ to SQL objektový Model
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: cc05166cffdd7254c657f0c490afaaac4cf08fcb
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="the-linq-to-sql-object-model"></a><span data-ttu-id="0b2e2-102">Technologie LINQ to SQL objektový Model</span><span class="sxs-lookup"><span data-stu-id="0b2e2-102">The LINQ to SQL Object Model</span></span>
<span data-ttu-id="0b2e2-103">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], vyjádřené v programovací jazyk vývojář objektový model je namapována na datový model relační databáze.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model expressed in the programming language of the developer is mapped to the data model of a relational database.</span></span> <span data-ttu-id="0b2e2-104">Operace s daty jsou pak provedeny podle modelu objektu.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-104">Operations on the data are then conducted according to the object model.</span></span>  
  
 <span data-ttu-id="0b2e2-105">V tomto scénáři není vydávat příkazy databáze (například `INSERT`) do databáze.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-105">In this scenario, you do not issue database commands (for example, `INSERT`) to the database.</span></span> <span data-ttu-id="0b2e2-106">Místo toho můžete změnit hodnoty a spouštět metody v rámci objektu modelu.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-106">Instead, you change values and execute methods within your object model.</span></span> <span data-ttu-id="0b2e2-107">Pokud chcete dotaz na databázi nebo odeslání se změní, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překládá své žádosti do správné příkazy SQL a odešle tyto příkazy do databáze.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-107">When you want to query the database or send it changes, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates your requests into the correct SQL commands and sends those commands to the database.</span></span>  
  
 <span data-ttu-id="0b2e2-108">![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")</span><span class="sxs-lookup"><span data-stu-id="0b2e2-108">![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")</span></span>  
  
 <span data-ttu-id="0b2e2-109">Většina základních elementů v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektový model a jejich vztahu k elementů ve model relačních dat jsou shrnuty v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="0b2e2-109">The most fundamental elements in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model and their relationship to elements in the relational data model are summarized in the following table:</span></span>  
  
|<span data-ttu-id="0b2e2-110">Technologie LINQ to SQL objektový Model</span><span class="sxs-lookup"><span data-stu-id="0b2e2-110">LINQ to SQL Object Model</span></span>|<span data-ttu-id="0b2e2-111">Relační datový Model</span><span class="sxs-lookup"><span data-stu-id="0b2e2-111">Relational Data Model</span></span>|  
|------------------------------|---------------------------|  
|<span data-ttu-id="0b2e2-112">Třídy entita</span><span class="sxs-lookup"><span data-stu-id="0b2e2-112">Entity class</span></span>|<span data-ttu-id="0b2e2-113">Tabulka</span><span class="sxs-lookup"><span data-stu-id="0b2e2-113">Table</span></span>|  
|<span data-ttu-id="0b2e2-114">Člen třídy</span><span class="sxs-lookup"><span data-stu-id="0b2e2-114">Class member</span></span>|<span data-ttu-id="0b2e2-115">Sloupec</span><span class="sxs-lookup"><span data-stu-id="0b2e2-115">Column</span></span>|  
|<span data-ttu-id="0b2e2-116">Přidružení</span><span class="sxs-lookup"><span data-stu-id="0b2e2-116">Association</span></span>|<span data-ttu-id="0b2e2-117">Cizí klíč relace</span><span class="sxs-lookup"><span data-stu-id="0b2e2-117">Foreign-key relationship</span></span>|  
|<span data-ttu-id="0b2e2-118">Metoda</span><span class="sxs-lookup"><span data-stu-id="0b2e2-118">Method</span></span>|<span data-ttu-id="0b2e2-119">Uložená procedura nebo funkce</span><span class="sxs-lookup"><span data-stu-id="0b2e2-119">Stored Procedure or Function</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="0b2e2-120">V následujících popisech Předpokládejme, že máte základní znalosti o relační datový model a pravidla.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-120">The following descriptions assume that you have a basic knowledge of the relational data model and rules.</span></span>  
  
## <a name="linq-to-sql-entity-classes-and-database-tables"></a><span data-ttu-id="0b2e2-121">Technologie LINQ to SQL Entity třídy a tabulek databáze</span><span class="sxs-lookup"><span data-stu-id="0b2e2-121">LINQ to SQL Entity Classes and Database Tables</span></span>  
 <span data-ttu-id="0b2e2-122">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], databázové tabulky je reprezentována *třídy entita*.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-122">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a database table is represented by an *entity class*.</span></span> <span data-ttu-id="0b2e2-123">Třídu entity je jako jiné třídy, které můžete vytvořit s tím rozdílem, že přidání poznámek ke třídě pomocí speciální informace, které přidružuje třída databázové tabulky.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-123">An entity class is like any other class you might create except that you annotate the class by using special information that associates the class with a database table.</span></span> <span data-ttu-id="0b2e2-124">Tato anotace provést přidáním vlastních atributů (<xref:System.Data.Linq.Mapping.TableAttribute>) do vaší deklaraci třídy, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0b2e2-124">You make this annotation by adding a custom attribute (<xref:System.Data.Linq.Mapping.TableAttribute>) to your class declaration, as in the following example:</span></span>  
  
### <a name="example"></a><span data-ttu-id="0b2e2-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b2e2-125">Example</span></span>  
 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 <span data-ttu-id="0b2e2-126">Pouze instance tříd deklarovaných jako tabulky (to znamená, tříd entit) lze uložit do databáze.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-126">Only instances of classes declared as tables (that is, entity classes) can be saved to the database.</span></span>  
  
 <span data-ttu-id="0b2e2-127">Další informace najdete v části atribut tabulky z [na základě atributů mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="0b2e2-127">For more information, see the Table Attribute section of [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
## <a name="linq-to-sql-class-members-and-database-columns"></a><span data-ttu-id="0b2e2-128">Technologie LINQ to SQL členy třídy a sloupců databáze</span><span class="sxs-lookup"><span data-stu-id="0b2e2-128">LINQ to SQL Class Members and Database Columns</span></span>  
 <span data-ttu-id="0b2e2-129">Kromě přiřazení třídy s tabulkami, určete pole nebo vlastnosti představují sloupců databáze.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-129">In addition to associating classes with tables, you designate fields or properties to represent database columns.</span></span> <span data-ttu-id="0b2e2-130">Pro tento účel [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] definuje <xref:System.Data.Linq.Mapping.ColumnAttribute> atributů, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0b2e2-130">For this purpose, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] defines the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute, as in the following example:</span></span>  
  
### <a name="example"></a><span data-ttu-id="0b2e2-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b2e2-131">Example</span></span>  
 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 <span data-ttu-id="0b2e2-132">Pouze polí a vlastností namapovaných na sloupce jsou uchovány v nebo načíst z databáze.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-132">Only fields and properties mapped to columns are persisted to or retrieved from the database.</span></span> <span data-ttu-id="0b2e2-133">Ty není deklarován jako sloupce jsou považovány za jako přechodný částí logiky aplikace.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-133">Those not declared as columns are considered as transient parts of your application logic.</span></span>  
  
 <span data-ttu-id="0b2e2-134"><xref:System.Data.Linq.Mapping.ColumnAttribute> Atribut má celou řadu vlastností, které můžete použít k přizpůsobení těchto členů, které představují sloupce (například určení člena jako představující sloupec primárního klíče).</span><span class="sxs-lookup"><span data-stu-id="0b2e2-134">The <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute has a variety of properties that you can use to customize these members that represent columns (for example, designating a member as representing a primary key column).</span></span> <span data-ttu-id="0b2e2-135">Další informace najdete v části atribut sloupce [na základě atributů mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="0b2e2-135">For more information, see the Column Attribute section of [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
## <a name="linq-to-sql-associations-and-database-foreign-key-relationships"></a><span data-ttu-id="0b2e2-136">Technologie LINQ to SQL přidružení a relace cizího klíče databáze</span><span class="sxs-lookup"><span data-stu-id="0b2e2-136">LINQ to SQL Associations and Database Foreign-key Relationships</span></span>  
 <span data-ttu-id="0b2e2-137">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], představují přidružení databáze (například cizího klíče do primárního klíče relace) s použitím <xref:System.Data.Linq.Mapping.AssociationAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-137">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you represent database associations (such as foreign-key to primary-key relationships) by applying the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span> <span data-ttu-id="0b2e2-138">V následující segmentu kódu `Order` třída obsahuje `Customer` vlastnost, která má <xref:System.Data.Linq.Mapping.AssociationAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-138">In the following segment of code, the `Order` class contains a `Customer` property that has an <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span> <span data-ttu-id="0b2e2-139">Tato vlastnost a jeho atribut poskytují `Order` třídy s relací k `Customer` třídy.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-139">This property and its attribute provide the `Order` class with a relationship to the `Customer` class.</span></span>  
  
 <span data-ttu-id="0b2e2-140">Následující příklad kódu ukazuje `Customer` vlastnost z `Order` třídy.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-140">The following code example shows the `Customer` property from the `Order` class.</span></span>  
  
### <a name="example"></a><span data-ttu-id="0b2e2-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b2e2-141">Example</span></span>  
 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 <span data-ttu-id="0b2e2-142">Další informace najdete v tématu části přidružení atribut [na základě atributů mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="0b2e2-142">For more information, see the Association Attribute section of [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
## <a name="linq-to-sql-methods-and-database-stored-procedures"></a><span data-ttu-id="0b2e2-143">Technologie LINQ to SQL metody a databáze uložené procedury</span><span class="sxs-lookup"><span data-stu-id="0b2e2-143">LINQ to SQL Methods and Database Stored Procedures</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="0b2e2-144"> podporuje uložené procedury a funkce definované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-144"> supports stored procedures and user-defined functions.</span></span> <span data-ttu-id="0b2e2-145">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], mapování těchto abstrakce definované databáze na objekty klienta, aby přístup jim silného typu způsobem z kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-145">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you map these database-defined abstractions to client objects so that you can access them in a strongly typed manner from client code.</span></span> <span data-ttu-id="0b2e2-146">Metoda podpisy podobat co možná nejvíce signatur procedury a funkce, které jsou definované v databázi.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-146">The method signatures resemble as closely as possible the signatures of the procedures and functions defined in the database.</span></span> <span data-ttu-id="0b2e2-147">IntelliSense můžete použít ke zjištění těchto metod.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-147">You can use IntelliSense to discover these methods.</span></span>  
  
 <span data-ttu-id="0b2e2-148">Výsledek, který je nastaven vrácené voláním namapované proceduře je silného typu kolekce.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-148">A result set that is returned by a call to a mapped procedure is a strongly typed collection.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="0b2e2-149"> mapuje uložené procedury a funkce metody pomocí <xref:System.Data.Linq.Mapping.FunctionAttribute> a <xref:System.Data.Linq.Mapping.ParameterAttribute> atributy.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-149"> maps stored procedures and functions to methods by using the <xref:System.Data.Linq.Mapping.FunctionAttribute> and <xref:System.Data.Linq.Mapping.ParameterAttribute> attributes.</span></span> <span data-ttu-id="0b2e2-150">Metody představující uložené procedury rozlišují od těch, představující uživatelsky definované funkce pomocí <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-150">Methods representing stored procedures are distinguished from those representing user-defined functions by the <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> property.</span></span> <span data-ttu-id="0b2e2-151">Pokud je tato vlastnost nastavena na `false` (výchozí), metoda představuje uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-151">If this property is set to `false` (the default), the method represents a stored procedure.</span></span> <span data-ttu-id="0b2e2-152">Pokud je nastaven na hodnotu `true`, metoda představuje funkce databáze.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-152">If it is set to `true`, the method represents a database function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b2e2-153">Pokud používáte Visual Studio, můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] k vytvoření metody, které jsou namapované na uložené procedury a uživatelem definované funkce.</span><span class="sxs-lookup"><span data-stu-id="0b2e2-153">If you are using Visual Studio, you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create methods mapped to stored procedures and user-defined functions.</span></span>  
  
### <a name="example"></a><span data-ttu-id="0b2e2-154">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b2e2-154">Example</span></span>  
 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 <span data-ttu-id="0b2e2-155">Další informace najdete v tématu na atribut funkce, uložené procedury atribut a atribut parametru části [na základě atributů mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) a [uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0b2e2-155">For more information, see the Function Attribute, Stored Procedure Attribute, and Parameter Attribute sections of [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) and [Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b2e2-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b2e2-156">See Also</span></span>  
 [<span data-ttu-id="0b2e2-157">Mapování na základě atributů</span><span class="sxs-lookup"><span data-stu-id="0b2e2-157">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [<span data-ttu-id="0b2e2-158">Základní informace</span><span class="sxs-lookup"><span data-stu-id="0b2e2-158">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
