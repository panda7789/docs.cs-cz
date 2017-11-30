---
title: "Model Entity Data Model: obory názvů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3e473453576f04e89b58806c5140e29855d7d022
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="entity-data-model-namespaces"></a><span data-ttu-id="6c2de-102">Model Entity Data Model: obory názvů</span><span class="sxs-lookup"><span data-stu-id="6c2de-102">Entity Data Model: Namespaces</span></span>
<span data-ttu-id="6c2de-103">Obor názvů v modelu Entity Data Model (EDM) je abstraktní kontejner pro [typy entit](../../../../docs/framework/data/adonet/entity-type.md), [komplexní typy](../../../../docs/framework/data/adonet/complex-type.md), a [přidružení](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="6c2de-103">A namespace in the Entity Data Model (EDM) is an abstract container for [entity types](../../../../docs/framework/data/adonet/entity-type.md), [complex types](../../../../docs/framework/data/adonet/complex-type.md), and [associations](../../../../docs/framework/data/adonet/association-type.md).</span></span> <span data-ttu-id="6c2de-104">Obory názvů v modelu EDM jsou podobná obory názvů v programovacím jazyce: poskytují kontext pro objekty, které obsahují a poskytují způsob k rozlišení objekty, které mají stejný název (ale jsou obsaženy v různých oborech názvů).</span><span class="sxs-lookup"><span data-stu-id="6c2de-104">Namespaces in the EDM are similar to namespaces in a programming language: they provide context for the objects that they contain and they provide a way to disambiguate objects that have the same name (but are contained in different namespaces).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c2de-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c2de-105">Example</span></span>  
 <span data-ttu-id="6c2de-106">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech.</span><span class="sxs-lookup"><span data-stu-id="6c2de-106">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="6c2de-107">Následující kód CSDL obor názvů používá k identifikaci typ, který je definován v různých konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="6c2de-107">The following CSDL code uses a namespace to identify a type that is defined in a different conceptual model.</span></span> <span data-ttu-id="6c2de-108">V příkladu je definován typ entity (`Publisher`), má vlastnost komplexního typu (`Address`) importovány z `ExtendedBooksModel` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6c2de-108">The example defines an entity type (`Publisher`) that has a complex type property (`Address`) that is imported from the `ExtendedBooksModel` namespace.</span></span> <span data-ttu-id="6c2de-109">Všimněte si, že `Using` element označuje, zda byla naimportována obor názvů.</span><span class="sxs-lookup"><span data-stu-id="6c2de-109">Note that the `Using` element indicates that a namespace has been imported.</span></span> <span data-ttu-id="6c2de-110">Všimněte si také, že typ `Address` vlastnost je definovaná pomocí plně kvalifikovaným názvem (`ExtendedBooksModel.Address`), což indikuje, že tento typ je definována v `ExtendedBooksModel` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6c2de-110">Also note that the type of the `Address` property is defined by using its fully qualified name (`ExtendedBooksModel.Address`), indicating that this type is defined in the `ExtendedBooksModel` namespace.</span></span>  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a><span data-ttu-id="6c2de-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c2de-111">See Also</span></span>  
 [<span data-ttu-id="6c2de-112">Entity Data Model klíčové koncepty</span><span class="sxs-lookup"><span data-stu-id="6c2de-112">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="6c2de-113">Datového modelu entity</span><span class="sxs-lookup"><span data-stu-id="6c2de-113">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
