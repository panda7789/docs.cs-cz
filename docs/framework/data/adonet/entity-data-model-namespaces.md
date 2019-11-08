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
# <a name="entity-data-model-namespaces"></a>Model EDM (Entity Data Model): obory názvů
Obor názvů v model EDM (Entity Data Model) (EDM) je abstraktní kontejner pro [typy entit](entity-type.md), [komplexní typy](complex-type.md)a [asociace](association-type.md). Obory názvů v modelu EDM jsou podobné oborům názvů v programovacím jazyce: poskytují kontext pro objekty, které obsahují, a poskytují způsob, jak určit, zda objekty mají stejný název (ale jsou obsaženy v různých oborech názvů).  
  
## <a name="example"></a>Příklad  
 [ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language). Následující kód CSDL používá obor názvů k identifikaci typu, který je definován v jiném koncepčním modelu. Příklad definuje typ entity (`Publisher`), která má vlastnost komplexního typu (`Address`), která je importována z oboru názvů `ExtendedBooksModel`. Všimněte si, že prvek `Using` označuje, že byl importován obor názvů. Všimněte si také, že typ vlastnosti `Address` je definován pomocí plně kvalifikovaného názvu (`ExtendedBooksModel.Address`), který označuje, že tento typ je definován v oboru názvů `ExtendedBooksModel`.  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)
