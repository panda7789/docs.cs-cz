---
title: entity key
ms.date: 03/30/2017
ms.assetid: 0d447a6d-fa7a-4db0-8e7a-fd45e385fca0
ms.openlocfilehash: 39a7500f088aa85baf0244005d6a804b3bf0b521
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737789"
---
# <a name="entity-key"></a>entity key
*Klíč entity* je [vlastnost](property.md) nebo sada vlastností [typu entity](entity-type.md) , které se používají k určení identity. Vlastnosti, které tvoří klíč entity, se volí v době návrhu. Hodnoty vlastností klíče entity musí jedinečně určovat instanci typu entity v [sadě entit](entity-set.md) za běhu. Pro zajištění jedinečnosti instancí v sadě entit by se měla zvolit vlastnosti, které tvoří klíč entity.  
  
 Níže jsou uvedeny požadavky na sadu vlastností na klíč entity:  
  
- Žádné dva klíče entit v sadě entit nemohou být identické. To znamená, že u všech dvou entit v sadě entit nemůže být hodnoty všech vlastností, které tvoří klíč, stejné. Některé (ale ne všechny) hodnoty, které tvoří klíč entity, ale mohou být stejné.  
  
- Klíč entity se musí skládat ze sady [vlastností primitivního typu](entity-data-model-primitive-data-types.md), které nejsou null, jsou neměnné.  
  
- Vlastnosti, které tvoří klíč entity pro daný typ entity, nelze změnit. Pro daný typ entity nelze povolen více než jeden klíč entity. náhradní klíče se nepodporují.  
  
- Pokud je entita zahrnuta v hierarchii dědičnosti, musí kořenová entita obsahovat všechny vlastnosti, které tvoří klíč entity, a klíč entity musí být definován pro typ kořenové entity. Další informace najdete v tématu [model EDM (Entity Data Model): dědičnost](entity-data-model-inheritance.md).  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje koncepční model se třemi typy entit: `Book`, `Publisher`a `Author`. Vlastnosti každého typu entity, který tvoří klíč entity, se označuje jako "(klíč)". Všimněte si, že typ entity `Author` obsahuje klíč entity, který se skládá ze dvou vlastností `Name` a `Address`.  
  
 ![Vzorový model se třemi typy entit](./media/entity-key/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language). Následující CSDL definuje typ entity `Book` zobrazený v diagramu výše. Všimněte si, že klíč entity je definován odkazem na vlastnost `ISBN` typu entity.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 Vlastnost `ISBN` je vhodnou volbou pro klíč entity, protože mezinárodní číslo knihy (ISBN) jednoznačně identifikuje knihu.  
  
 Následující CSDL definuje typ entity `Author` zobrazený v diagramu výše. Všimněte si, že klíč entity se skládá ze dvou vlastností `Name` a `Address`.  
  
 [!code-xml[EDM_Example_Model#CompositeKeyExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#compositekeyexample)]  
  
 Použití `Name` a `Address` pro klíč entity je rozumnou volbou, protože dva autoři se stejným názvem pravděpodobně nebudou v provozu na stejné adrese. Tato volba pro klíč entity ale v sadě entit naprosto nezaručuje jedinečné klíče entit. V tomto případě se doporučuje přidat vlastnost, jako je například `AuthorId`, kterou by bylo možné použít k jednoznačné identifikaci autora.  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)
