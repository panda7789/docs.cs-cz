---
title: Model EDM (Entity Data Model) Jmenné prostory
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: a8629a1f162f5d942390f62d5a2ac20e2135c531
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784014"
---
# <a name="entity-data-model-namespaces"></a><span data-ttu-id="241a7-102">Model EDM (Entity Data Model) Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="241a7-102">Entity Data Model: Namespaces</span></span>
<span data-ttu-id="241a7-103">Obor názvů v model EDM (Entity Data Model) (EDM) je abstraktní kontejner pro [typy entit](entity-type.md), [komplexní typy](complex-type.md)a [asociace](association-type.md).</span><span class="sxs-lookup"><span data-stu-id="241a7-103">A namespace in the Entity Data Model (EDM) is an abstract container for [entity types](entity-type.md), [complex types](complex-type.md), and [associations](association-type.md).</span></span> <span data-ttu-id="241a7-104">Obory názvů v modelu EDM jsou podobné oborům názvů v programovacím jazyce: poskytují kontext pro objekty, které obsahují, a poskytují způsob, jak určit, zda objekty mají stejný název (ale jsou obsaženy v různých oborech názvů).</span><span class="sxs-lookup"><span data-stu-id="241a7-104">Namespaces in the EDM are similar to namespaces in a programming language: they provide context for the objects that they contain and they provide a way to disambiguate objects that have the same name (but are contained in different namespaces).</span></span>  
  
## <a name="example"></a><span data-ttu-id="241a7-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="241a7-105">Example</span></span>  
 <span data-ttu-id="241a7-106">[ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](./ef/language-reference/csdl-specification.md)(konceptuální schéma Definition Language).</span><span class="sxs-lookup"><span data-stu-id="241a7-106">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="241a7-107">Následující kód CSDL používá obor názvů k identifikaci typu, který je definován v jiném koncepčním modelu.</span><span class="sxs-lookup"><span data-stu-id="241a7-107">The following CSDL code uses a namespace to identify a type that is defined in a different conceptual model.</span></span> <span data-ttu-id="241a7-108">Příklad definuje typ entity (`Publisher`), která má vlastnost komplexního typu (`Address`) `ExtendedBooksModel` , která je importována z oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="241a7-108">The example defines an entity type (`Publisher`) that has a complex type property (`Address`) that is imported from the `ExtendedBooksModel` namespace.</span></span> <span data-ttu-id="241a7-109">Všimněte si, `Using` že element označuje, že byl importován obor názvů.</span><span class="sxs-lookup"><span data-stu-id="241a7-109">Note that the `Using` element indicates that a namespace has been imported.</span></span> <span data-ttu-id="241a7-110">Všimněte si také, že typ `Address` vlastnosti je definován pomocí jeho plně kvalifikovaného názvu (`ExtendedBooksModel.Address`), což značí, že tento `ExtendedBooksModel` typ je definován v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="241a7-110">Also note that the type of the `Address` property is defined by using its fully qualified name (`ExtendedBooksModel.Address`), indicating that this type is defined in the `ExtendedBooksModel` namespace.</span></span>  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a><span data-ttu-id="241a7-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="241a7-111">See also</span></span>

- [<span data-ttu-id="241a7-112">Koncepty modelu EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="241a7-112">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="241a7-113">Model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="241a7-113">Entity Data Model</span></span>](entity-data-model.md)
