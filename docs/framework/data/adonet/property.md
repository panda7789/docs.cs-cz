---
title: property
ms.date: 03/30/2017
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
ms.openlocfilehash: d1e20a6570c458041ec5d8ececbfa291ca9e4612
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735391"
---
# <a name="property"></a>property
*Vlastnosti* jsou základní stavební bloky [typů entit](entity-type.md) a [komplexních typů](complex-type.md). Vlastnosti definují tvar a vlastnosti dat, které bude obsahovat instance typu entity nebo instance komplexního typu. Vlastnosti v koncepčním modelu jsou analogické k vlastnostem definovaným pro třídu. Stejně jako vlastnosti třídy definují tvar třídy a přenášejí informace o objektech, vlastnosti v koncepčním modelu definují tvar typu entity a přenášejí informace o instancích typu entity.  
  
> [!NOTE]
> Vlastnosti, jak je popsáno v tomto tématu, se liší od vlastností navigace. Další informace najdete v tématu [vlastnosti navigace](navigation-property.md).  
  
 Definice vlastnosti obsahuje následující informace:  
  
- Název vlastnosti. Požadovanou  
  
- Typ vlastnosti. Požadovanou  
  
- Sada [omezujících vlastností](facet.md). Volitelné  
  
 Vlastnost může obsahovat primitivní data (například řetězec, celé číslo nebo logickou hodnotu) nebo strukturovaná data (například komplexní typ). Vlastnosti primitivního typu jsou označovány také jako skalární vlastnosti. Další informace naleznete v tématu [model EDM (Entity Data Model): primitivní datové typy](entity-data-model-primitive-data-types.md).  
  
> [!NOTE]
> Komplexní typ může sám sebe mít vlastnosti, které jsou komplexní typy.  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje koncepční model se třemi typy entit: `Book`, `Publisher`a `Author`. Každý typ entity má několik vlastností, i když informace o typech jednotlivých vlastností nejsou v diagramu předány. Vlastnosti, které jsou [klíče entit](entity-key.md) , se označuje jako (klíč).  
  
 ![Vzorový model se třemi typy entit](./media/property/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language). Následující soubor CSDL definuje typ entity `Book` (jak je znázorněno v diagramu výše) a označuje typ a název každé vlastnosti pomocí atributů XML. Volitelná omezující vlastnost, `Nullable`, je definována také pomocí atributu XML.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 Je možné, že jedna z vlastností zobrazených v diagramu je vlastnost komplexního typu. Například vlastnost `Address` v typu entity `Publisher` by mohla být vlastnost komplexního typu složená z několika skalárních vlastností, jako jsou například `StreetAddress`, `City`, `StateOrProvince`, `Country`a `PostalCode`. Reprezentace typu CSDL takového komplexního typu by vypadala takto:  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)
