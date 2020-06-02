---
title: Entity Data Model
description: Model EDM (Entity Data Model) popisuje strukturu dat bez ohledu na jeho uložený tvar, který řeší výzvy vyplývající z ukládání dat v mnoha formulářích.
ms.date: 03/30/2017
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
ms.openlocfilehash: c98b1f4559ef297f8b11051940fd91f5f6fa06fd
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286737"
---
# <a name="entity-data-model"></a><span data-ttu-id="45e27-103">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="45e27-103">Entity Data Model</span></span>
<span data-ttu-id="45e27-104">Model EDM (Entity Data Model) (EDM) je sada konceptů popisujících strukturu dat bez ohledu na její uložený formulář.</span><span class="sxs-lookup"><span data-stu-id="45e27-104">The Entity Data Model (EDM) is a set of concepts that describe the structure of data, regardless of its stored form.</span></span> <span data-ttu-id="45e27-105">EDM se vypůjčuje z modelu vztahů mezi entitami, který popisuje Petr Chen ve 1976, ale také vytvoří model vztahů mezi entitami a rozšiřuje tradiční použití.</span><span class="sxs-lookup"><span data-stu-id="45e27-105">The EDM borrows from the Entity-Relationship Model described by Peter Chen in 1976, but it also builds on the Entity-Relationship Model and extends its traditional uses.</span></span>  
  
 <span data-ttu-id="45e27-106">EDM řeší výzvy, které vzniknou z dat uložených v mnoha formulářích.</span><span class="sxs-lookup"><span data-stu-id="45e27-106">The EDM addresses the challenges that arise from having data stored in many forms.</span></span> <span data-ttu-id="45e27-107">Představte si třeba firmu, která ukládá data v relačních databázích, textových souborech, souborech XML, tabulkách a sestavách.</span><span class="sxs-lookup"><span data-stu-id="45e27-107">For example, consider a business that stores data in relational databases, text files, XML files, spreadsheets, and reports.</span></span> <span data-ttu-id="45e27-108">To představuje významné problémy při modelování dat, návrhu aplikací a přístupu k datům.</span><span class="sxs-lookup"><span data-stu-id="45e27-108">This presents significant challenges in data modeling, application design, and data access.</span></span> <span data-ttu-id="45e27-109">Při navrhování aplikace orientované na data je nutné, aby bylo možné zapisovat do efektivního a udržovatelného kódu, aniž byste se museli vzdát efektivního přístupu k datům, úložiště a škálovatelnosti.</span><span class="sxs-lookup"><span data-stu-id="45e27-109">When designing a data-oriented application, the challenge is to write efficient and maintainable code without sacrificing efficient data access, storage, and scalability.</span></span> <span data-ttu-id="45e27-110">Když data mají relační strukturu, přístup k datům, úložiště a škálovatelnost jsou velmi efektivní, ale psaní efektivního a udržovatelného kódu se bude obtížnější.</span><span class="sxs-lookup"><span data-stu-id="45e27-110">When data has a relational structure, data access, storage, and scalability are very efficient, but writing efficient and maintainable code becomes more difficult.</span></span> <span data-ttu-id="45e27-111">Když data obsahují strukturu objektu, probíhající se kompromisy: zápis efektivního a udržovatelného kódu se účtuje za cenu efektivního přístupu k datům, úložiště a škálovatelnosti.</span><span class="sxs-lookup"><span data-stu-id="45e27-111">When data has an object structure, the trade-offs are reversed: Writing efficient and maintainable code comes at the cost of efficient data access, storage, and scalability.</span></span> <span data-ttu-id="45e27-112">I v případě, že je možné najít správné saldo mezi těmito kompromisy, vzniknou nové výzvy při přesunu dat z jednoho formuláře do druhého.</span><span class="sxs-lookup"><span data-stu-id="45e27-112">Even if the right balance between these trade-offs can be found, new challenges arise when data is moved from one form to another.</span></span> <span data-ttu-id="45e27-113">Model EDM (Entity Data Model) řeší tyto výzvy tím, že popisuje strukturu dat z pohledu entit a vztahy, které jsou nezávislé na jakémkoli schématu úložiště.</span><span class="sxs-lookup"><span data-stu-id="45e27-113">The Entity Data Model addresses these challenges by describing the structure of data in terms of entities and relationships that are independent of any storage schema.</span></span> <span data-ttu-id="45e27-114">Díky tomu je uložená forma dat irelevantní pro návrh a vývoj aplikací.</span><span class="sxs-lookup"><span data-stu-id="45e27-114">This makes the stored form of data irrelevant to application design and development.</span></span> <span data-ttu-id="45e27-115">A vzhledem k tomu, že entity a vztahy popisují strukturu dat, která se používají v aplikaci (ne v její uložené podobě), můžou se vyvíjet jako vývoj aplikace.</span><span class="sxs-lookup"><span data-stu-id="45e27-115">And, because entities and relationships describe the structure of data as it is used in an application (not its stored form), they can evolve as an application evolves.</span></span>  
  
 <span data-ttu-id="45e27-116">A `conceptual model` je konkrétní reprezentace struktury dat jako entit a vztahů a je obecně definována v jazyce specifickém pro doménu (DSL), který implementuje koncepty modelu EDM.</span><span class="sxs-lookup"><span data-stu-id="45e27-116">A `conceptual model` is a specific representation of the structure of data as entities and relationships, and is generally defined in a domain-specific language (DSL) that implements the concepts of the EDM.</span></span> <span data-ttu-id="45e27-117">[Konceptuální schéma definiční jazyk (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec) je příkladem konkrétního jazyka specifického pro doménu.</span><span class="sxs-lookup"><span data-stu-id="45e27-117">[Conceptual schema definition language (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec) is an example of such a domain-specific language.</span></span> <span data-ttu-id="45e27-118">Entity a vztahy, které jsou popsány v koncepčním modelu, lze představit jako abstrakce objektů a přidružení v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="45e27-118">Entities and relationships described in a conceptual model can be thought of as abstractions of objects and associations in an application.</span></span> <span data-ttu-id="45e27-119">To umožňuje vývojářům soustředit se na koncepční model bez obav o schéma úložiště a umožňuje jim psát kód s efektivitou a udržovatelnosti.</span><span class="sxs-lookup"><span data-stu-id="45e27-119">This allows developers to focus on the conceptual model without concern for the storage schema, and allows them to write code with efficiency and maintainability in mind.</span></span> <span data-ttu-id="45e27-120">Díky sestupným návrhářům schémat úložiště se můžete soustředit na efektivitu přístupu k datům, úložiště a škálovatelnosti.</span><span class="sxs-lookup"><span data-stu-id="45e27-120">Meanwhile storage schema designers can focus on the efficiency of data access, storage, and scalability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45e27-121">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="45e27-121">In This Section</span></span>  
 <span data-ttu-id="45e27-122">Témata v této části popisují koncepty model EDM (Entity Data Model).</span><span class="sxs-lookup"><span data-stu-id="45e27-122">Topics in this section describe the concepts of the Entity Data Model.</span></span> <span data-ttu-id="45e27-123">Všechny DSL, které implementují EDM, by měly obsahovat koncepty popsané tady.</span><span class="sxs-lookup"><span data-stu-id="45e27-123">Any DSL that implements the EDM should include the concepts described here.</span></span> <span data-ttu-id="45e27-124">Všimněte si, že [ADO.NET Entity Framework](./ef/index.md) používá CSDL k definování konceptuálních modelů.</span><span class="sxs-lookup"><span data-stu-id="45e27-124">Note that the [ADO.NET Entity Framework](./ef/index.md) uses CSDL to define conceptual models.</span></span> <span data-ttu-id="45e27-125">Další informace najdete v tématu [specifikace CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).</span><span class="sxs-lookup"><span data-stu-id="45e27-125">For more information, see [CSDL Specification](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).</span></span>  
  
 [<span data-ttu-id="45e27-126">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="45e27-126">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)  
  
 [<span data-ttu-id="45e27-127">Model EDM (Entity Data Model): Obory názvů</span><span class="sxs-lookup"><span data-stu-id="45e27-127">Entity Data Model: Namespaces</span></span>](entity-data-model-namespaces.md)  
  
 [<span data-ttu-id="45e27-128">Model EDM (Entity Data Model): Primitivní datové typy</span><span class="sxs-lookup"><span data-stu-id="45e27-128">Entity Data Model: Primitive Data Types</span></span>](entity-data-model-primitive-data-types.md)  
  
 [<span data-ttu-id="45e27-129">Model EDM (Entity Data Model): Dědičnost</span><span class="sxs-lookup"><span data-stu-id="45e27-129">Entity Data Model: Inheritance</span></span>](entity-data-model-inheritance.md)  
  
 [<span data-ttu-id="45e27-130">association end</span><span class="sxs-lookup"><span data-stu-id="45e27-130">association end</span></span>](association-end.md)  
  
 [<span data-ttu-id="45e27-131">association end multiplicity</span><span class="sxs-lookup"><span data-stu-id="45e27-131">association end multiplicity</span></span>](association-end-multiplicity.md)  
  
 [<span data-ttu-id="45e27-132">association set</span><span class="sxs-lookup"><span data-stu-id="45e27-132">association set</span></span>](association-set.md)  
  
 [<span data-ttu-id="45e27-133">association set end</span><span class="sxs-lookup"><span data-stu-id="45e27-133">association set end</span></span>](association-set-end.md)  
  
 [<span data-ttu-id="45e27-134">association type</span><span class="sxs-lookup"><span data-stu-id="45e27-134">association type</span></span>](association-type.md)  
  
 [<span data-ttu-id="45e27-135">complex type</span><span class="sxs-lookup"><span data-stu-id="45e27-135">complex type</span></span>](complex-type.md)  
  
 [<span data-ttu-id="45e27-136">entity container</span><span class="sxs-lookup"><span data-stu-id="45e27-136">entity container</span></span>](entity-container.md)  
  
 [<span data-ttu-id="45e27-137">entity key</span><span class="sxs-lookup"><span data-stu-id="45e27-137">entity key</span></span>](entity-key.md)  
  
 [<span data-ttu-id="45e27-138">entity set</span><span class="sxs-lookup"><span data-stu-id="45e27-138">entity set</span></span>](entity-set.md)  
  
 [<span data-ttu-id="45e27-139">entity type</span><span class="sxs-lookup"><span data-stu-id="45e27-139">entity type</span></span>](entity-type.md)  
  
 [<span data-ttu-id="45e27-140">omezující vlastnost</span><span class="sxs-lookup"><span data-stu-id="45e27-140">facet</span></span>](facet.md)  
  
 [<span data-ttu-id="45e27-141">foreign key property</span><span class="sxs-lookup"><span data-stu-id="45e27-141">foreign key property</span></span>](foreign-key-property.md)  
  
 [<span data-ttu-id="45e27-142">model-declared function</span><span class="sxs-lookup"><span data-stu-id="45e27-142">model-declared function</span></span>](model-declared-function.md)  
  
 [<span data-ttu-id="45e27-143">model-defined function</span><span class="sxs-lookup"><span data-stu-id="45e27-143">model-defined function</span></span>](model-defined-function.md)  
  
 [<span data-ttu-id="45e27-144">navigation property</span><span class="sxs-lookup"><span data-stu-id="45e27-144">navigation property</span></span>](navigation-property.md)  
  
 [<span data-ttu-id="45e27-145">majetek</span><span class="sxs-lookup"><span data-stu-id="45e27-145">property</span></span>](property.md)  
  
 [<span data-ttu-id="45e27-146">referential integrity constraint</span><span class="sxs-lookup"><span data-stu-id="45e27-146">referential integrity constraint</span></span>](referential-integrity-constraint.md)  
  
## <a name="see-also"></a><span data-ttu-id="45e27-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="45e27-147">See also</span></span>

- <span data-ttu-id="45e27-148">[ADO.NET model EDM (Entity Data Model) nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="45e27-148">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="45e27-149">[Soubor. edmx – přehled](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="45e27-149">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="45e27-150">Specifikace CSDL</span><span class="sxs-lookup"><span data-stu-id="45e27-150">CSDL Specification</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
