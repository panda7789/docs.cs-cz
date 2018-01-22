---
title: Entity Data Model
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e1a1bdeffcc85383d241c277240187ede41401cd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="entity-data-model"></a><span data-ttu-id="ab7c5-102">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="ab7c5-102">Entity Data Model</span></span>
<span data-ttu-id="ab7c5-103">Entity Data Model (EDM) je sada koncepty, které popisují strukturu dat, bez ohledu na jeho uložené formuláře.</span><span class="sxs-lookup"><span data-stu-id="ab7c5-103">The Entity Data Model (EDM) is a set of concepts that describe the structure of data, regardless of its stored form.</span></span> <span data-ttu-id="ab7c5-104">Vychází z modelu vztah entit popsaného Petr Svoboda v 1976 jazyků EDM, ale také založený na modelu vztah entit a rozšiřuje jeho tradiční používá.</span><span class="sxs-lookup"><span data-stu-id="ab7c5-104">The EDM borrows from the Entity-Relationship Model described by Peter Chen in 1976, but it also builds on the Entity-Relationship Model and extends its traditional uses.</span></span>  
  
 <span data-ttu-id="ab7c5-105">EDM řeší problémy, které způsobit s daty uloženými v celou řadu forem.</span><span class="sxs-lookup"><span data-stu-id="ab7c5-105">The EDM addresses the challenges that arise from having data stored in many forms.</span></span> <span data-ttu-id="ab7c5-106">Představte si třeba firmy, která ukládá data v relačních databází, textové soubory, soubory XML, tabulky a sestavy.</span><span class="sxs-lookup"><span data-stu-id="ab7c5-106">For example, consider a business that stores data in relational databases, text files, XML files, spreadsheets, and reports.</span></span> <span data-ttu-id="ab7c5-107">To představuje významné problémy v datech modelování, návrh aplikace a přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="ab7c5-107">This presents significant challenges in data modeling, application design, and data access.</span></span> <span data-ttu-id="ab7c5-108">Při navrhování aplikace data, na výzvu je napsat kód efektivní a udržovatelný bez omezení přístupu k datům efektivní, úložiště a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="ab7c5-108">When designing a data-oriented application, the challenge is to write efficient and maintainable code without sacrificing efficient data access, storage, and scalability.</span></span> <span data-ttu-id="ab7c5-109">Pokud data má relační strukturu, jsou velmi efektivní přístup k datům, úložiště a škálovatelnost, ale zápis efektivní a udržovatelného kódu je podstatně obtížnější.</span><span class="sxs-lookup"><span data-stu-id="ab7c5-109">When data has a relational structure, data access, storage, and scalability are very efficient, but writing efficient and maintainable code becomes more difficult.</span></span> <span data-ttu-id="ab7c5-110">Pokud data strukturu objekt, jsou kompromisy vrátit: psaní kódu efektivní a udržovatelný dodává za cenu přístup k datům efektivní, úložiště a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="ab7c5-110">When data has an object structure, the trade-offs are reversed: Writing efficient and maintainable code comes at the cost of efficient data access, storage, and scalability.</span></span> <span data-ttu-id="ab7c5-111">I když můžete najít rovnováhu mezi tyto kompromisy, vyvolány další výzvy při přesunutí dat z jednoho formátu do jiného.</span><span class="sxs-lookup"><span data-stu-id="ab7c5-111">Even if the right balance between these trade-offs can be found, new challenges arise when data is moved from one form to another.</span></span> <span data-ttu-id="ab7c5-112">Datový Model Entity řeší tyto problémy prostřednictvím popisu strukturu dat z hlediska entity a vztahy, které jsou nezávislé na žádné schéma úložiště.</span><span class="sxs-lookup"><span data-stu-id="ab7c5-112">The Entity Data Model addresses these challenges by describing the structure of data in terms of entities and relationships that are independent of any storage schema.</span></span> <span data-ttu-id="ab7c5-113">Díky tomu uložené formu dat. důležité aplikace návrh a vývoj.</span><span class="sxs-lookup"><span data-stu-id="ab7c5-113">This makes the stored form of data irrelevant to application design and development.</span></span> <span data-ttu-id="ab7c5-114">A protože entity a vztahy popisují strukturu dat, protože se používá v aplikaci (ne jeho uložené formulář), můžete rozvíjet jako zpracovaní aplikace.</span><span class="sxs-lookup"><span data-stu-id="ab7c5-114">And, because entities and relationships describe the structure of data as it is used in an application (not its stored form), they can evolve as an application evolves.</span></span>  
  
 <span data-ttu-id="ab7c5-115">A `conceptual model` je konkrétní reprezentace strukturu dat jako entity a vztahy a je obvykle definováno v jazyce specifické pro doménu (DSL), který implementuje koncepty EDM.</span><span class="sxs-lookup"><span data-stu-id="ab7c5-115">A `conceptual model` is a specific representation of the structure of data as entities and relationships, and is generally defined in a domain-specific language (DSL) that implements the concepts of the EDM.</span></span> <span data-ttu-id="ab7c5-116">[Koncepční schéma definition language (CSDL)](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) je příkladem jazyk specifické pro doménu.</span><span class="sxs-lookup"><span data-stu-id="ab7c5-116">[Conceptual schema definition language (CSDL)](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) is an example of such a domain-specific language.</span></span> <span data-ttu-id="ab7c5-117">Entity a vztahy, které jsou popsané v konceptuálním modelu lze považovat za abstrakce objektů a přidružení v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ab7c5-117">Entities and relationships described in a conceptual model can be thought of as abstractions of objects and associations in an application.</span></span> <span data-ttu-id="ab7c5-118">To umožňuje vývojářům soustředit na konceptuální model bez obav o schéma úložiště a umožňuje je napsat kód s efektivitu a jeho udržovatelnost v paměti.</span><span class="sxs-lookup"><span data-stu-id="ab7c5-118">This allows developers to focus on the conceptual model without concern for the storage schema, and allows them to write code with efficiency and maintainability in mind.</span></span> <span data-ttu-id="ab7c5-119">Mezitím Designer schéma úložiště můžete soustředit na efektivitu přístup k datům, úložiště a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="ab7c5-119">Meanwhile storage schema designers can focus on the efficiency of data access, storage, and scalability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ab7c5-120">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ab7c5-120">In This Section</span></span>  
 <span data-ttu-id="ab7c5-121">Témata v této části popisují koncepty datového modelu Entity.</span><span class="sxs-lookup"><span data-stu-id="ab7c5-121">Topics in this section describe the concepts of the Entity Data Model.</span></span> <span data-ttu-id="ab7c5-122">Všechny DSL, který implementuje EDM by měla obsahovat konceptů popsaných v tomto poli.</span><span class="sxs-lookup"><span data-stu-id="ab7c5-122">Any DSL that implements the EDM should include the concepts described here.</span></span> <span data-ttu-id="ab7c5-123">Všimněte si, že [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) CSDL používá k definování konceptuálních modelech.</span><span class="sxs-lookup"><span data-stu-id="ab7c5-123">Note that the [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses CSDL to define conceptual models.</span></span> <span data-ttu-id="ab7c5-124">Další informace najdete v tématu [CSDL specifikace](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).</span><span class="sxs-lookup"><span data-stu-id="ab7c5-124">For more information, see [CSDL Specification](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).</span></span>  
  
 [<span data-ttu-id="ab7c5-125">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="ab7c5-125">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
  
 [<span data-ttu-id="ab7c5-126">Model EDM (Entity Data Model): Obory názvů</span><span class="sxs-lookup"><span data-stu-id="ab7c5-126">Entity Data Model: Namespaces</span></span>](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md)  
  
 [<span data-ttu-id="ab7c5-127">Model EDM (Entity Data Model): Primitivní datové typy</span><span class="sxs-lookup"><span data-stu-id="ab7c5-127">Entity Data Model: Primitive Data Types</span></span>](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)  
  
 [<span data-ttu-id="ab7c5-128">Model EDM (Entity Data Model): Dědičnost</span><span class="sxs-lookup"><span data-stu-id="ab7c5-128">Entity Data Model: Inheritance</span></span>](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)  
  
 [<span data-ttu-id="ab7c5-129">association end</span><span class="sxs-lookup"><span data-stu-id="ab7c5-129">association end</span></span>](../../../../docs/framework/data/adonet/association-end.md)  
  
 [<span data-ttu-id="ab7c5-130">association end multiplicity</span><span class="sxs-lookup"><span data-stu-id="ab7c5-130">association end multiplicity</span></span>](../../../../docs/framework/data/adonet/association-end-multiplicity.md)  
  
 [<span data-ttu-id="ab7c5-131">association set</span><span class="sxs-lookup"><span data-stu-id="ab7c5-131">association set</span></span>](../../../../docs/framework/data/adonet/association-set.md)  
  
 [<span data-ttu-id="ab7c5-132">association set end</span><span class="sxs-lookup"><span data-stu-id="ab7c5-132">association set end</span></span>](../../../../docs/framework/data/adonet/association-set-end.md)  
  
 [<span data-ttu-id="ab7c5-133">association type</span><span class="sxs-lookup"><span data-stu-id="ab7c5-133">association type</span></span>](../../../../docs/framework/data/adonet/association-type.md)  
  
 [<span data-ttu-id="ab7c5-134">complex type</span><span class="sxs-lookup"><span data-stu-id="ab7c5-134">complex type</span></span>](../../../../docs/framework/data/adonet/complex-type.md)  
  
 [<span data-ttu-id="ab7c5-135">entity container</span><span class="sxs-lookup"><span data-stu-id="ab7c5-135">entity container</span></span>](../../../../docs/framework/data/adonet/entity-container.md)  
  
 [<span data-ttu-id="ab7c5-136">entity key</span><span class="sxs-lookup"><span data-stu-id="ab7c5-136">entity key</span></span>](../../../../docs/framework/data/adonet/entity-key.md)  
  
 [<span data-ttu-id="ab7c5-137">entity set</span><span class="sxs-lookup"><span data-stu-id="ab7c5-137">entity set</span></span>](../../../../docs/framework/data/adonet/entity-set.md)  
  
 [<span data-ttu-id="ab7c5-138">entity type</span><span class="sxs-lookup"><span data-stu-id="ab7c5-138">entity type</span></span>](../../../../docs/framework/data/adonet/entity-type.md)  
  
 [<span data-ttu-id="ab7c5-139">facet</span><span class="sxs-lookup"><span data-stu-id="ab7c5-139">facet</span></span>](../../../../docs/framework/data/adonet/facet.md)  
  
 [<span data-ttu-id="ab7c5-140">foreign key property</span><span class="sxs-lookup"><span data-stu-id="ab7c5-140">foreign key property</span></span>](../../../../docs/framework/data/adonet/foreign-key-property.md)  
  
 [<span data-ttu-id="ab7c5-141">model-declared function</span><span class="sxs-lookup"><span data-stu-id="ab7c5-141">model-declared function</span></span>](../../../../docs/framework/data/adonet/model-declared-function.md)  
  
 [<span data-ttu-id="ab7c5-142">model-defined function</span><span class="sxs-lookup"><span data-stu-id="ab7c5-142">model-defined function</span></span>](../../../../docs/framework/data/adonet/model-defined-function.md)  
  
 [<span data-ttu-id="ab7c5-143">navigation property</span><span class="sxs-lookup"><span data-stu-id="ab7c5-143">navigation property</span></span>](../../../../docs/framework/data/adonet/navigation-property.md)  
  
 [<span data-ttu-id="ab7c5-144">property</span><span class="sxs-lookup"><span data-stu-id="ab7c5-144">property</span></span>](../../../../docs/framework/data/adonet/property.md)  
  
 [<span data-ttu-id="ab7c5-145">referential integrity constraint</span><span class="sxs-lookup"><span data-stu-id="ab7c5-145">referential integrity constraint</span></span>](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)  
  
## <a name="see-also"></a><span data-ttu-id="ab7c5-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab7c5-146">See Also</span></span>  
 [<span data-ttu-id="ab7c5-147">Nástroje modelu ADO.NET Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="ab7c5-147">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)  
 [<span data-ttu-id="ab7c5-148">Přehled souboru EDMX</span><span class="sxs-lookup"><span data-stu-id="ab7c5-148">.edmx File Overview</span></span>](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="ab7c5-149">Specifikace CSDL</span><span class="sxs-lookup"><span data-stu-id="ab7c5-149">CSDL Specification</span></span>](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)
