---
title: property
ms.date: 03/30/2017
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
ms.openlocfilehash: 80c4bb3ccbab75c17b098723fc10b8b996e40576
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409715"
---
# <a name="property"></a>property
*Vlastnosti* jsou základní stavební kameny [typy entit](../../../../docs/framework/data/adonet/entity-type.md) a [komplexní typy](../../../../docs/framework/data/adonet/complex-type.md). Vlastnosti definovat tvar a vlastnosti dat, která bude obsahovat instance typu entity nebo komplexní typ instance. Vlastnosti v konceptuálním modelu jsou podobná vlastnosti definované ve třídě. Stejným způsobem, že vlastnosti třídy definovat tvar třídy a budou mít informace o objektech vlastnosti v konceptuálním modelu definovat tvar typu entity a nesou informaci o instancí typu entity.  
  
> [!NOTE]
>  Vlastnosti, jak je popsáno v tomto tématu, se liší od navigační vlastnosti. Další informace najdete v tématu [navigační vlastnosti](../../../../docs/framework/data/adonet/navigation-property.md).  
  
 Definice vlastnosti obsahuje následující informace:  
  
-   Název vlastnosti. (Povinné)  
  
-   Typ vlastnosti. (Povinné)  
  
-   Sada [omezující vlastnosti](../../../../docs/framework/data/adonet/facet.md). (Volitelné)  
  
 Vlastnost může obsahovat primitivní datové (například řetězec, celé číslo nebo hodnotu typu Boolean) nebo strukturovaná data (například komplexní typ). Vlastnosti, které jsou primitivního typu se také označují jako skalární vlastnosti. Další informace najdete v tématu [modelu Entity Data Model: Primitivní datové typy](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).  
  
> [!NOTE]
>  Komplexní typ, samotný, mají vlastnosti, které jsou komplexní typy.  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model s tři typy entit: `Book`, `Publisher`, a `Author`. Každý typ entity má několik vlastností, i když se předávají informace o typu pro každou vlastnost v diagramu. Vlastnosti, které jsou [klíče entit](../../../../docs/framework/data/adonet/entity-key.md) jsou rozlišeny pomocí (klíč).  
  
 ![Příklad modelu s tři typy entit](./media/property/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů. Definuje následující CSDL `Book` entity typu (jak je uvedeno ve výše uvedeném diagramu) a určuje typ a název každé vlastnosti pomocí atributů XML. Volitelné omezující vlastnost, `Nullable`, je také definován pomocí atribut XML.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 Je možné, že jedna z vlastností je zobrazeno na diagramu je vlastností komplexního typu. Například `Address` vlastnost `Publisher` typ entity může být komplexního typu vlastnosti, který se skládá z několika Skalární vlastnosti, jako například `StreetAddress`, `City`, `StateOrProvince`, `Country`, a `PostalCode`. Reprezentace CSDL komplexní typ by měl vypadat takto:  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a>Viz také:
- [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)
