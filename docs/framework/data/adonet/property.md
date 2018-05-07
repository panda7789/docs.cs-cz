---
title: property
ms.date: 03/30/2017
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
ms.openlocfilehash: 2476aef13da6424d0d8c58bdd1e37a72df29d8a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="property"></a>property
*Vlastnosti* jsou základní stavební kameny [typy entit](../../../../docs/framework/data/adonet/entity-type.md) a [komplexní typy](../../../../docs/framework/data/adonet/complex-type.md). Vlastnosti definovat tvar a vlastnosti dat, která bude obsahovat instance typu entity nebo komplexního typu. Vlastnosti v konceptuálním modelu jsou podobná vlastnosti definované na třídu. Stejným způsobem, že vlastnosti třídy definovat tvaru třídy a provádění informace o objektech vlastnosti v konceptuálním modelu definovat obrazce typu entity a provádění informace o instancích typu entity.  
  
> [!NOTE]
>  Vlastnosti, jak je popsáno v tomto tématu se liší od navigační vlastnosti. Další informace najdete v tématu [navigační vlastnosti](../../../../docs/framework/data/adonet/navigation-property.md).  
  
 Definici vlastnosti obsahuje následující informace:  
  
-   Název vlastnosti. (Povinné)  
  
-   Typ vlastnosti. (Povinné)  
  
-   Sadu [omezující vlastnosti](../../../../docs/framework/data/adonet/facet.md). (Volitelné)  
  
 Vlastnost může obsahovat primitivní datové (například řetězec, celé číslo nebo logická hodnota) nebo strukturovaná data (například komplexního typu). Vlastnosti, které jsou primitivního typu se také označují jako skalární vlastnosti. Další informace najdete v tématu [datového modelu Entity: primitivní datové typy](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).  
  
> [!NOTE]
>  Komplexní typ můžou mít sama, vlastnosti, které jsou komplexní typy.  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model se tři typy entit: `Book`, `Publisher`, a `Author`. Každý typ entity má několik vlastností, i když bude v diagramu není předávat informace o typu pro každou vlastnost. Vlastnosti, které jsou [klíče entit](../../../../docs/framework/data/adonet/entity-key.md) , jsou označeny (klíč).  
  
 ![Ukázkový Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech. Definuje následující CSDL `Book` entity zadejte (jak je znázorněno na obrázku výš) a určuje typ a název každé vlastnosti pomocí atributů jazyka XML. Volitelné omezující vlastnosti, `Nullable`, je také definován pomocí atribut XML.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 Je možné, že jedna z vlastností vidět na obrázku je vlastnost komplexního typu. Například `Address` vlastnost `Publisher` typ entity může být komplexní typ vlastnosti, který se skládá z několika Skalární vlastnosti, jako například `StreetAddress`, `City`, `StateOrProvince`, `Country`, a `PostalCode`. Reprezentace CSDL komplexního typu vypadat takto:  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a>Viz také  
 [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)
