---
title: Model EDM (Entity Data Model) Jmenné prostory
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: 7772172512d35b9ce9cf07a992c1c5f0ecd8c55b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667155"
---
# <a name="entity-data-model-namespaces"></a>Model EDM (Entity Data Model) Jmenné prostory
Obor názvů v modelu Entity Data Model (EDM) je abstraktní kontejner pro [typy entit](../../../../docs/framework/data/adonet/entity-type.md), [komplexní typy](../../../../docs/framework/data/adonet/complex-type.md), a [přidružení](../../../../docs/framework/data/adonet/association-type.md). Obory názvů v modelu EDM jsou podobné pro obory názvů v programovacím jazyce: poskytuje kontext pro objekty, které obsahují a poskytují způsob k rozlišení objektů, které mají stejný název (ale jsou obsaženy v různých oborech názvů).  
  
## <a name="example"></a>Příklad  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů. Následující kód CSDL obor názvů používá k identifikaci typ, který je definován v jiné konceptuálního modelu. V příkladu je definován typ entity (`Publisher`), který má vlastnost komplexní typ (`Address`), která je importována z `ExtendedBooksModel` oboru názvů. Všimněte si, že `Using` element označuje, že se importovala oboru názvů. Všimněte si také, že typ `Address` vlastnost je definována pomocí jeho plně kvalifikovaný název (`ExtendedBooksModel.Address`), označující, že tento typ je definován v `ExtendedBooksModel` oboru názvů.  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)
