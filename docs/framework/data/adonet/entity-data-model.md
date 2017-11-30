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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 69b72a824e6f9468c9b3d86073243d506382e766
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="entity-data-model"></a><span data-ttu-id="6a40d-102">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="6a40d-102">Entity Data Model</span></span>
<span data-ttu-id="6a40d-103">Entity Data Model (EDM) je sada koncepty, které popisují strukturu dat, bez ohledu na jeho uložené formuláře.</span><span class="sxs-lookup"><span data-stu-id="6a40d-103">The Entity Data Model (EDM) is a set of concepts that describe the structure of data, regardless of its stored form.</span></span> <span data-ttu-id="6a40d-104">Vychází z modelu vztah entit popsaného Petr Svoboda v 1976 jazyků EDM, ale také založený na modelu vztah entit a rozšiřuje jeho tradiční používá.</span><span class="sxs-lookup"><span data-stu-id="6a40d-104">The EDM borrows from the Entity-Relationship Model described by Peter Chen in 1976, but it also builds on the Entity-Relationship Model and extends its traditional uses.</span></span>  
  
 <span data-ttu-id="6a40d-105">EDM řeší problémy, které způsobit s daty uloženými v celou řadu forem.</span><span class="sxs-lookup"><span data-stu-id="6a40d-105">The EDM addresses the challenges that arise from having data stored in many forms.</span></span> <span data-ttu-id="6a40d-106">Představte si třeba firmy, která ukládá data v relačních databází, textové soubory, soubory XML, tabulky a sestavy.</span><span class="sxs-lookup"><span data-stu-id="6a40d-106">For example, consider a business that stores data in relational databases, text files, XML files, spreadsheets, and reports.</span></span> <span data-ttu-id="6a40d-107">To představuje významné problémy v datech modelování, návrh aplikace a přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="6a40d-107">This presents significant challenges in data modeling, application design, and data access.</span></span> <span data-ttu-id="6a40d-108">Při navrhování aplikace data, na výzvu je napsat kód efektivní a udržovatelný bez omezení přístupu k datům efektivní, úložiště a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="6a40d-108">When designing a data-oriented application, the challenge is to write efficient and maintainable code without sacrificing efficient data access, storage, and scalability.</span></span> <span data-ttu-id="6a40d-109">Pokud data má relační strukturu, jsou velmi efektivní přístup k datům, úložiště a škálovatelnost, ale zápis efektivní a udržovatelného kódu je podstatně obtížnější.</span><span class="sxs-lookup"><span data-stu-id="6a40d-109">When data has a relational structure, data access, storage, and scalability are very efficient, but writing efficient and maintainable code becomes more difficult.</span></span> <span data-ttu-id="6a40d-110">Pokud data strukturu objekt, jsou kompromisy vrátit: psaní kódu efektivní a udržovatelný dodává za cenu přístup k datům efektivní, úložiště a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="6a40d-110">When data has an object structure, the trade-offs are reversed: Writing efficient and maintainable code comes at the cost of efficient data access, storage, and scalability.</span></span> <span data-ttu-id="6a40d-111">I když můžete najít rovnováhu mezi tyto kompromisy, vyvolány další výzvy při přesunutí dat z jednoho formátu do jiného.</span><span class="sxs-lookup"><span data-stu-id="6a40d-111">Even if the right balance between these trade-offs can be found, new challenges arise when data is moved from one form to another.</span></span> <span data-ttu-id="6a40d-112">Datový Model Entity řeší tyto problémy prostřednictvím popisu strukturu dat z hlediska entity a vztahy, které jsou nezávislé na žádné schéma úložiště.</span><span class="sxs-lookup"><span data-stu-id="6a40d-112">The Entity Data Model addresses these challenges by describing the structure of data in terms of entities and relationships that are independent of any storage schema.</span></span> <span data-ttu-id="6a40d-113">Díky tomu uložené formu dat. důležité aplikace návrh a vývoj.</span><span class="sxs-lookup"><span data-stu-id="6a40d-113">This makes the stored form of data irrelevant to application design and development.</span></span> <span data-ttu-id="6a40d-114">A protože entity a vztahy popisují strukturu dat, protože se používá v aplikaci (ne jeho uložené formulář), můžete rozvíjet jako zpracovaní aplikace.</span><span class="sxs-lookup"><span data-stu-id="6a40d-114">And, because entities and relationships describe the structure of data as it is used in an application (not its stored form), they can evolve as an application evolves.</span></span>  
  
 <span data-ttu-id="6a40d-115">A `conceptual model` je konkrétní reprezentace strukturu dat jako entity a vztahy a je obvykle definováno v jazyce specifické pro doménu (DSL), který implementuje koncepty EDM.</span><span class="sxs-lookup"><span data-stu-id="6a40d-115">A `conceptual model` is a specific representation of the structure of data as entities and relationships, and is generally defined in a domain-specific language (DSL) that implements the concepts of the EDM.</span></span> <span data-ttu-id="6a40d-116">[Koncepční schéma definition language (CSDL)](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) je příkladem jazyk specifické pro doménu.</span><span class="sxs-lookup"><span data-stu-id="6a40d-116">[Conceptual schema definition language (CSDL)](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) is an example of such a domain-specific language.</span></span> <span data-ttu-id="6a40d-117">Entity a vztahy, které jsou popsané v konceptuálním modelu lze považovat za abstrakce objektů a přidružení v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6a40d-117">Entities and relationships described in a conceptual model can be thought of as abstractions of objects and associations in an application.</span></span> <span data-ttu-id="6a40d-118">To umožňuje vývojářům soustředit na konceptuální model bez obav o schéma úložiště a umožňuje je napsat kód s efektivitu a jeho udržovatelnost v paměti.</span><span class="sxs-lookup"><span data-stu-id="6a40d-118">This allows developers to focus on the conceptual model without concern for the storage schema, and allows them to write code with efficiency and maintainability in mind.</span></span> <span data-ttu-id="6a40d-119">Mezitím Designer schéma úložiště můžete soustředit na efektivitu přístup k datům, úložiště a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="6a40d-119">Meanwhile storage schema designers can focus on the efficiency of data access, storage, and scalability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6a40d-120">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6a40d-120">In This Section</span></span>  
 <span data-ttu-id="6a40d-121">Témata v této části popisují koncepty datového modelu Entity.</span><span class="sxs-lookup"><span data-stu-id="6a40d-121">Topics in this section describe the concepts of the Entity Data Model.</span></span> <span data-ttu-id="6a40d-122">Všechny DSL, který implementuje EDM by měla obsahovat konceptů popsaných v tomto poli.</span><span class="sxs-lookup"><span data-stu-id="6a40d-122">Any DSL that implements the EDM should include the concepts described here.</span></span> <span data-ttu-id="6a40d-123">Všimněte si, že [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) CSDL používá k definování konceptuálních modelech.</span><span class="sxs-lookup"><span data-stu-id="6a40d-123">Note that the [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses CSDL to define conceptual models.</span></span> <span data-ttu-id="6a40d-124">Další informace najdete v tématu [CSDL specifikace](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).</span><span class="sxs-lookup"><span data-stu-id="6a40d-124">For more information, see [CSDL Specification](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).</span></span>  
  
 [<span data-ttu-id="6a40d-125">Entity Data Model klíčové koncepty</span><span class="sxs-lookup"><span data-stu-id="6a40d-125">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
  
 [<span data-ttu-id="6a40d-126">Model Entity Data Model: obory názvů</span><span class="sxs-lookup"><span data-stu-id="6a40d-126">Entity Data Model: Namespaces</span></span>](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md)  
  
 [<span data-ttu-id="6a40d-127">Datového modelu entity: Primitivní datové typy</span><span class="sxs-lookup"><span data-stu-id="6a40d-127">Entity Data Model: Primitive Data Types</span></span>](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)  
  
 [<span data-ttu-id="6a40d-128">Model Entity Data Model: dědičnosti</span><span class="sxs-lookup"><span data-stu-id="6a40d-128">Entity Data Model: Inheritance</span></span>](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)  
  
 [<span data-ttu-id="6a40d-129">end přidružení</span><span class="sxs-lookup"><span data-stu-id="6a40d-129">association end</span></span>](../../../../docs/framework/data/adonet/association-end.md)  
  
 [<span data-ttu-id="6a40d-130">násobnost end přidružení</span><span class="sxs-lookup"><span data-stu-id="6a40d-130">association end multiplicity</span></span>](../../../../docs/framework/data/adonet/association-end-multiplicity.md)  
  
 [<span data-ttu-id="6a40d-131">Sada přidružení</span><span class="sxs-lookup"><span data-stu-id="6a40d-131">association set</span></span>](../../../../docs/framework/data/adonet/association-set.md)  
  
 [<span data-ttu-id="6a40d-132">konce přidružení sady</span><span class="sxs-lookup"><span data-stu-id="6a40d-132">association set end</span></span>](../../../../docs/framework/data/adonet/association-set-end.md)  
  
 [<span data-ttu-id="6a40d-133">Typ přidružení</span><span class="sxs-lookup"><span data-stu-id="6a40d-133">association type</span></span>](../../../../docs/framework/data/adonet/association-type.md)  
  
 [<span data-ttu-id="6a40d-134">komplexní typ</span><span class="sxs-lookup"><span data-stu-id="6a40d-134">complex type</span></span>](../../../../docs/framework/data/adonet/complex-type.md)  
  
 [<span data-ttu-id="6a40d-135">kontejneru entit</span><span class="sxs-lookup"><span data-stu-id="6a40d-135">entity container</span></span>](../../../../docs/framework/data/adonet/entity-container.md)  
  
 [<span data-ttu-id="6a40d-136">klíč entity</span><span class="sxs-lookup"><span data-stu-id="6a40d-136">entity key</span></span>](../../../../docs/framework/data/adonet/entity-key.md)  
  
 [<span data-ttu-id="6a40d-137">sada entit</span><span class="sxs-lookup"><span data-stu-id="6a40d-137">entity set</span></span>](../../../../docs/framework/data/adonet/entity-set.md)  
  
 [<span data-ttu-id="6a40d-138">Typ entity</span><span class="sxs-lookup"><span data-stu-id="6a40d-138">entity type</span></span>](../../../../docs/framework/data/adonet/entity-type.md)  
  
 [<span data-ttu-id="6a40d-139">omezující vlastnost</span><span class="sxs-lookup"><span data-stu-id="6a40d-139">facet</span></span>](../../../../docs/framework/data/adonet/facet.md)  
  
 [<span data-ttu-id="6a40d-140">vlastností cizího klíče</span><span class="sxs-lookup"><span data-stu-id="6a40d-140">foreign key property</span></span>](../../../../docs/framework/data/adonet/foreign-key-property.md)  
  
 [<span data-ttu-id="6a40d-141">deklarovaný modelu – funkce</span><span class="sxs-lookup"><span data-stu-id="6a40d-141">model-declared function</span></span>](../../../../docs/framework/data/adonet/model-declared-function.md)  
  
 [<span data-ttu-id="6a40d-142">model definované funkce</span><span class="sxs-lookup"><span data-stu-id="6a40d-142">model-defined function</span></span>](../../../../docs/framework/data/adonet/model-defined-function.md)  
  
 [<span data-ttu-id="6a40d-143">navigační vlastnost</span><span class="sxs-lookup"><span data-stu-id="6a40d-143">navigation property</span></span>](../../../../docs/framework/data/adonet/navigation-property.md)  
  
 [<span data-ttu-id="6a40d-144">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="6a40d-144">property</span></span>](../../../../docs/framework/data/adonet/property.md)  
  
 [<span data-ttu-id="6a40d-145">omezení referenční integrity</span><span class="sxs-lookup"><span data-stu-id="6a40d-145">referential integrity constraint</span></span>](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)  
  
## <a name="see-also"></a><span data-ttu-id="6a40d-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a40d-146">See Also</span></span>  
 [<span data-ttu-id="6a40d-147">Nástroje modelu ADO.NET Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="6a40d-147">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)  
 [<span data-ttu-id="6a40d-148">Přehled souboru EDMX</span><span class="sxs-lookup"><span data-stu-id="6a40d-148">.edmx File Overview</span></span>](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="6a40d-149">Specifikace CSDL</span><span class="sxs-lookup"><span data-stu-id="6a40d-149">CSDL Specification</span></span>](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)
