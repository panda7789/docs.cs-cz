---
title: entity key
ms.date: 03/30/2017
ms.assetid: 0d447a6d-fa7a-4db0-8e7a-fd45e385fca0
ms.openlocfilehash: 1484a73450d5a435f795f18f122c7fe8494cf197
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59140111"
---
# <a name="entity-key"></a>entity key
*Klíč entity* je [vlastnost](../../../../docs/framework/data/adonet/property.md) nebo sada vlastností [typ entity](../../../../docs/framework/data/adonet/entity-type.md) , který slouží k určení identity. Vlastnosti, které tvoří klíč entity jsou vybrán v době návrhu. Hodnoty vlastnosti klíče entity musí jednoznačně identifikovat instanci entity typu v rámci [sadu entit](../../../../docs/framework/data/adonet/entity-set.md) v době běhu. Vlastnosti, které tvoří klíč entity, je třeba zvolit pro zajištění jedinečnosti instancí v sadu entit.  
  
 Následují požadavky na sadu vlastností pro být klíč entity:  
  
-   Žádné klíče dvě entity v rámci sady entit může být identické. To znamená pro dvě entity v rámci sady entit, hodnoty pro všechny vlastnosti, které tvoří klíč nemůže být stejné. Nicméně některé (ale ne všech) hodnot, které tvoří entitu klíč může být stejný.  
  
-   Klíč entity musí obsahovat sadu Null, nezměnitelný, [primitivní typ vlastnosti](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).  
  
-   Vlastnosti, které tvoří klíč entity pro danou entitu typu nelze změnit. Více než jeden klíč možné entity nelze povolit pro danou entitu typu; náhradní klíče nejsou podporovány.  
  
-   Když entitu je zahrnuta v hierarchii dědičnosti, kořenové entity musí obsahovat všechny vlastnosti, které tvoří klíč entity a klíč entity musí být definováno na kořenový typ entity. Další informace najdete v tématu [modelu Entity Data Model: Dědičnost](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model s tři typy entit: `Book`, `Publisher`, a `Author`. Vlastnosti každého typu entity, které tvoří jeho klíč entity, jsou označeny "(klíč)". Všimněte si, že `Author` typ entity má klíč entity, která se skládá ze dvou vlastností `Name` a `Address`.  
  
 ![Příklad modelu s tři typy entit](./media/entity-key/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů. Definuje CSDL níže `Book` typ entity, které jsou zobrazeny ve výše uvedeném diagramu. Všimněte si, že je klíč entity definován odkazováním `ISBN` vlastnost typu entity.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 `ISBN` Vlastnost je dobrou volbou pro klíč entity, protože mezinárodní čísla pro standardní knihy (ISBN) jednoznačně identifikuje knihy.  
  
 Definuje CSDL níže `Author` typ entity, které jsou zobrazeny ve výše uvedeném diagramu. Všimněte si, že klíč entity se skládá ze dvou vlastností `Name` a `Address`.  
  
 [!code-xml[EDM_Example_Model#CompositeKeyExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#compositekeyexample)]  
  
 Pomocí `Name` a `Address` entity klíč je vhodná volba, protože je nepravděpodobné, že za provozu na stejné adrese dvě autoři se stejným názvem. Nicméně tato volba pro klíč entity naprosto nezaručuje klíče jedinečné entity v sadě entit. Přidání vlastnosti, jako například `AuthorId`, který může použít k jednoznačné identifikaci Autor by v tomto případě doporučujeme.  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)
