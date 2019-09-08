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
# <a name="entity-data-model-namespaces"></a>Model EDM (Entity Data Model) Jmenné prostory
Obor názvů v model EDM (Entity Data Model) (EDM) je abstraktní kontejner pro [typy entit](entity-type.md), [komplexní typy](complex-type.md)a [asociace](association-type.md). Obory názvů v modelu EDM jsou podobné oborům názvů v programovacím jazyce: poskytují kontext pro objekty, které obsahují, a poskytují způsob, jak určit, zda objekty mají stejný název (ale jsou obsaženy v různých oborech názvů).  
  
## <a name="example"></a>Příklad  
 [ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](./ef/language-reference/csdl-specification.md)(konceptuální schéma Definition Language). Následující kód CSDL používá obor názvů k identifikaci typu, který je definován v jiném koncepčním modelu. Příklad definuje typ entity (`Publisher`), která má vlastnost komplexního typu (`Address`) `ExtendedBooksModel` , která je importována z oboru názvů. Všimněte si, `Using` že element označuje, že byl importován obor názvů. Všimněte si také, že typ `Address` vlastnosti je definován pomocí jeho plně kvalifikovaného názvu (`ExtendedBooksModel.Address`), což značí, že tento `ExtendedBooksModel` typ je definován v oboru názvů.  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)
