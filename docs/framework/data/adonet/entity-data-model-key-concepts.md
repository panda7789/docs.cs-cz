---
title: Entity Data Model klíčové koncepty
ms.date: 03/30/2017
ms.assetid: c635a16d-6674-45aa-9344-dcb7df992bab
ms.openlocfilehash: d92d2a99562c7eac6fef0ba76cd00241d600c265
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765630"
---
# <a name="entity-data-model-key-concepts"></a>Entity Data Model klíčové koncepty
Entity Data Model (EDM) používá tři klíčové koncepty k popisu struktury dat: *typ entity*, *typ přidružení*, a *vlastnost*. Jedná se o nejdůležitějších konceptů v popisující strukturu dat v jakékoli použití EDM.  
  
## <a name="entity-type"></a>Typ entity  
 [Typ entity](../../../../docs/framework/data/adonet/entity-type.md) je základní stavební blok pro popisující strukturu dat s datovým modelem Entity. V konceptuálním modelu typy entit se vytvářejí na základě [vlastnosti](../../../../docs/framework/data/adonet/property.md) a popisují strukturu nejvyšší úrovně koncepty, jako jsou zákazníci a objednávky v obchodní aplikace. Stejným způsobem, že definice třídy v počítačový program je šablona pro instance třídy, je typ entity šablonu pro entity. Představuje entitu určitý objekt (například konkrétního zákazníka nebo pořadí). Každá entita musí mít jedinečnou [klíč entity](../../../../docs/framework/data/adonet/entity-key.md) v rámci [sady entit](../../../../docs/framework/data/adonet/entity-set.md).  Sadu entit je kolekce instancí určitý typ entity. Sad entit (a [přidružení sady](../../../../docs/framework/data/adonet/association-set.md)) jsou logicky seskupeny do [kontejneru entit](../../../../docs/framework/data/adonet/entity-container.md).  
  
 Dědičnost se podporuje s typy entit: jeden typ entity to znamená, může být odvozen z jiné. Další informace najdete v tématu [datového modelu Entity: dědičnosti](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).  
  
## <a name="association-type"></a>Typ přidružení  
 [Typ přidružení](../../../../docs/framework/data/adonet/association-type.md) (také nazývané přidružení) je základní stavební blok pro popis vztahů v datovém modelu Entity. Přidružení v konceptuálním modelu představuje vztah mezi dvěma typy entit (například zákazníka a pořadí). Každý přidružení má dva [zakončení přidružení](../../../../docs/framework/data/adonet/association-end.md) , zadejte účastnící se přidružení typy entit. Každý end přidružení určuje také [násobnost end přidružení](../../../../docs/framework/data/adonet/association-end-multiplicity.md) určující počet entit, které mohou být na tomto konci tohoto přidružení. Násobnost end přidružení může mít hodnotu jedna (1), žádnou nebo jednu (0..1), nebo mnoho (*). Entit na jednom konci přidružení je možné přistupovat prostřednictvím [navigační vlastnosti](../../../../docs/framework/data/adonet/navigation-property.md), nebo prostřednictvím cizí klíče, pokud jsou zveřejněné na typ entity. Další informace najdete v tématu [vlastností cizího klíče](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
 V aplikaci představuje instanci přidružení konkrétní přidružení (například přidružení mezi instanci zákazníka a instancí pořadí). Přidružení instance jsou logicky seskupeny do [sadu přidružení](../../../../docs/framework/data/adonet/association-set.md). Přidružení sady (a [sad entit](../../../../docs/framework/data/adonet/entity-set.md)) jsou logicky seskupeny do [kontejneru entit](../../../../docs/framework/data/adonet/entity-container.md).  
  
## <a name="property"></a>Vlastnost  
 [Typy entit](../../../../docs/framework/data/adonet/entity-type.md) obsahovat [vlastnosti](../../../../docs/framework/data/adonet/property.md) které definují jejich strukturu a vlastnosti. Například typu entity zákazníka může mít vlastnosti, například CustomerId, název a adresu.  
  
 Jsou obdobou vlastnosti definované na třídu v počítačový program vlastnosti v konceptuálním modelu. Stejným způsobem, že vlastnosti třídy definovat tvaru třídy a provádění informace o objektech vlastnosti v konceptuálním modelu definovat obrazce typu entity a provádění informace o instancích typu entity.  
  
 Vlastnost může obsahovat primitivní datové (například řetězec, celé číslo nebo logická hodnota) nebo strukturovaná data (například komplexního typu). Další informace najdete v tématu [datového modelu Entity: primitivní datové typy](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).  
  
## <a name="representations-of-a-conceptual-model"></a>Reprezentace konceptuálního modelu  
 A *konceptuálního modelu* je konkrétní reprezentace strukturu některá data jako entity a vztahy. Jedním ze způsobů představují konceptuálního modelu je s diagram. Následující diagram představuje konceptuální model se tři typy entit (`Book`, `Publisher`, a `Author`) a dvě přidružení (`PublishedBy` a `WrittenBy`):  
  
 ![Modelu s navigační vlastnosti](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")  
  
 Tento zápis, má však některé nedostatků při rozhodování o zdůraznění některé podrobnosti o modelu. Například vlastnost typu a entit sadu informace nejsou vyjádřeným v diagramu. Bohatost konceptuálního modelu může být bude zřetelněji předávat s jazykem specifické pro doménu (DSL). [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá formátu XML DSL názvem *konceptuálního schématu definice jazyka* ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech. Toto je definici CSDL konceptuálního modelu ve výše uvedeném diagramu:  
  
 [!code-xml[EDM_Example_Model#EDMExampleCSDL](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#edmexamplecsdl)]  
  
## <a name="see-also"></a>Viz také  
 [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)
