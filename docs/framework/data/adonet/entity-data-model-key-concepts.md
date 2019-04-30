---
title: Koncepty modelu EDM (Entity Data Model)
ms.date: 03/30/2017
ms.assetid: c635a16d-6674-45aa-9344-dcb7df992bab
ms.openlocfilehash: 2efa54b6bd656129812cc9dd7c2ce38a4fb2a89a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879269"
---
# <a name="entity-data-model-key-concepts"></a>Koncepty modelu EDM (Entity Data Model)
Entity Data Model (EDM) používá k popisu struktury dat tři klíčové koncepty: *typ entity*, *typ přidružení*, a *vlastnost*. Jedná se o nejdůležitějších pojmů v popisu struktury dat v jakékoli implementaci modelu EDM.  
  
## <a name="entity-type"></a>Typ entity  
 [Typ entity](../../../../docs/framework/data/adonet/entity-type.md) je základním stavebním blokem pro popis struktury data pomocí modelu Entity Data Model. V konceptuálním modelu typy entit se vytvářejí na základě [vlastnosti](../../../../docs/framework/data/adonet/property.md) a popisu struktury koncepty nejvyšší úrovně, jako je například Zákazníci a objednávky v podnikových aplikací. Stejným způsobem, že definice třídy v počítačový program je šablona pro instance třídy, typ entity je šablona pro entity. Entita představuje konkrétní objekt (například konkrétního zákazníka nebo pořadí). Každá entita musí mít jedinečnou [klíč entity](../../../../docs/framework/data/adonet/entity-key.md) v rámci [sadu entit](../../../../docs/framework/data/adonet/entity-set.md).  Sadu entit je kolekci instancí typu konkrétní entity. Sady entit (a [sad přidružení](../../../../docs/framework/data/adonet/association-set.md)) jsou logicky seskupeny do [kontejneru entity](../../../../docs/framework/data/adonet/entity-container.md).  
  
 Dědičnost je podporované prostřednictvím typů entit: jeden typ entity tedy může být odvozena z jiného. Další informace najdete v tématu [modelu Entity Data Model: Dědičnost](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).  
  
## <a name="association-type"></a>Typ přidružení  
 [Typ přidružení](../../../../docs/framework/data/adonet/association-type.md) (také nazývané přidružení) je základním stavebním blokem popisující relace v modelu Entity Data Model. Přidružení v konceptuálním modelu, představuje vztah mezi dvěma typy entit (jako je například odběratele a objednávky). Každé přidružení má dva [zakončení](../../../../docs/framework/data/adonet/association-end.md) , které určují typy entit, která je součástí přidružení. Každý end přidružení určuje také [násobnost end přidružení](../../../../docs/framework/data/adonet/association-end-multiplicity.md) , která určuje počet entit, které může být na této straně asociace. Násobnost end přidružení může mít hodnotě jedna (1), žádný nebo jeden (0..1), nebo mnoho (*). Entity na jednom konci asociace je přístupná prostřednictvím [navigační vlastnosti](../../../../docs/framework/data/adonet/navigation-property.md), nebo prostřednictvím cizí klíče, pokud jsou zveřejněné na typ entity. Další informace najdete v tématu [vlastnost cizího klíče](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
 V aplikaci, která představuje instance přidružení konkrétní přidružení (například přidružení mezi instance zákazníka a instance pořadí). Přidružení instance jsou logicky seskupeny do [sada přidružení](../../../../docs/framework/data/adonet/association-set.md). Přidružení sad (a [sad entit](../../../../docs/framework/data/adonet/entity-set.md)) jsou logicky seskupeny do [kontejneru entity](../../../../docs/framework/data/adonet/entity-container.md).  
  
## <a name="property"></a>Vlastnost  
 [Typy entit](../../../../docs/framework/data/adonet/entity-type.md) obsahovat [vlastnosti](../../../../docs/framework/data/adonet/property.md) , které definují jejich strukturu a vlastnosti. Například typ entity zákazník může mít vlastnosti, jako je ID zákazníka, název a adresu.  
  
 Vlastnosti v konceptuálním modelu jsou podobná vlastnosti definované ve třídě v počítačový program. Stejným způsobem, že vlastnosti třídy definovat tvar třídy a budou mít informace o objektech vlastnosti v konceptuálním modelu definovat tvar typu entity a nesou informaci o instancí typu entity.  
  
 Vlastnost může obsahovat primitivní datové (například řetězec, celé číslo nebo hodnotu typu Boolean) nebo strukturovaná data (například komplexní typ). Další informace najdete v tématu [modelu Entity Data Model: Primitivní datové typy](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).  
  
## <a name="representations-of-a-conceptual-model"></a>Reprezentace konceptuálního modelu  
 A *koncepčního modelu* je konkrétní reprezentace struktura některá data jako entit a vztahů. Jeden způsob, jak reprezentaci konceptuálního modelu je diagram. Následující diagram znázorňuje Koncepční model s tři typy entit (`Book`, `Publisher`, a `Author`) a dvě přidružení (`PublishedBy` a `WrittenBy`):  
  
 ![Diagram znázorňující konceptuálního modelu s tři typy entit.](./media/entity-data-model-key-concepts/conceptual-model-entity-types-associations.gif)  
  
 Tento zápis, má ale některé nedostatky při rozhodování o takzvané některé podrobnosti o tomto modelu. Například se předávají informace o nastavení vlastnosti typu a entit v diagramu. Bohatost konceptuálního modelu můžete jasněji předávají pomocí jazyka specifického pro doménu (DSL). [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá založený na formátu XML DSL, která volá *Konceptuální schéma definici jazyka* ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů. Toto je CSDL definici konceptuálního modelu ve výše uvedeném diagramu:  
  
 [!code-xml[EDM_Example_Model#EDMExampleCSDL](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#edmexamplecsdl)]  
  
## <a name="see-also"></a>Viz také:

- [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)
