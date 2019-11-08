---
title: 'Model EDM (Entity Data Model): obory názvů'
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: a403bcd459005ed9cea4a455fcde40c31c8caac9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738438"
---
# <a name="entity-data-model-namespaces"></a><span data-ttu-id="1771e-102">Model EDM (Entity Data Model): obory názvů</span><span class="sxs-lookup"><span data-stu-id="1771e-102">Entity Data Model: Namespaces</span></span>
<span data-ttu-id="1771e-103">Obor názvů v model EDM (Entity Data Model) (EDM) je abstraktní kontejner pro [typy entit](entity-type.md), [komplexní typy](complex-type.md)a [asociace](association-type.md).</span><span class="sxs-lookup"><span data-stu-id="1771e-103">A namespace in the Entity Data Model (EDM) is an abstract container for [entity types](entity-type.md), [complex types](complex-type.md), and [associations](association-type.md).</span></span> <span data-ttu-id="1771e-104">Obory názvů v modelu EDM jsou podobné oborům názvů v programovacím jazyce: poskytují kontext pro objekty, které obsahují, a poskytují způsob, jak určit, zda objekty mají stejný název (ale jsou obsaženy v různých oborech názvů).</span><span class="sxs-lookup"><span data-stu-id="1771e-104">Namespaces in the EDM are similar to namespaces in a programming language: they provide context for the objects that they contain and they provide a way to disambiguate objects that have the same name (but are contained in different namespaces).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1771e-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="1771e-105">Example</span></span>  
 <span data-ttu-id="1771e-106">[ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language).</span><span class="sxs-lookup"><span data-stu-id="1771e-106">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="1771e-107">Následující kód CSDL používá obor názvů k identifikaci typu, který je definován v jiném koncepčním modelu.</span><span class="sxs-lookup"><span data-stu-id="1771e-107">The following CSDL code uses a namespace to identify a type that is defined in a different conceptual model.</span></span> <span data-ttu-id="1771e-108">Příklad definuje typ entity (`Publisher`), která má vlastnost komplexního typu (`Address`), která je importována z oboru názvů `ExtendedBooksModel`.</span><span class="sxs-lookup"><span data-stu-id="1771e-108">The example defines an entity type (`Publisher`) that has a complex type property (`Address`) that is imported from the `ExtendedBooksModel` namespace.</span></span> <span data-ttu-id="1771e-109">Všimněte si, že prvek `Using` označuje, že byl importován obor názvů.</span><span class="sxs-lookup"><span data-stu-id="1771e-109">Note that the `Using` element indicates that a namespace has been imported.</span></span> <span data-ttu-id="1771e-110">Všimněte si také, že typ vlastnosti `Address` je definován pomocí plně kvalifikovaného názvu (`ExtendedBooksModel.Address`), který označuje, že tento typ je definován v oboru názvů `ExtendedBooksModel`.</span><span class="sxs-lookup"><span data-stu-id="1771e-110">Also note that the type of the `Address` property is defined by using its fully qualified name (`ExtendedBooksModel.Address`), indicating that this type is defined in the `ExtendedBooksModel` namespace.</span></span>  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a><span data-ttu-id="1771e-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1771e-111">See also</span></span>

- [<span data-ttu-id="1771e-112">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="1771e-112">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="1771e-113">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="1771e-113">Entity Data Model</span></span>](entity-data-model.md)
