---
title: Koncepty modelu EDM (Entity Data Model)
ms.date: 03/30/2017
ms.assetid: c635a16d-6674-45aa-9344-dcb7df992bab
ms.openlocfilehash: 5e4fc0c960d7dac289852df3b080c7e49d1d1c10
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795559"
---
# <a name="entity-data-model-key-concepts"></a>Koncepty modelu EDM (Entity Data Model)
Model EDM (Entity Data Model) (EDM) používá tři klíčové koncepty pro popis struktury dat: *typ entity*, *typ přidružení*a *vlastnost*. Jedná se o nejdůležitější koncepty v popisu struktury dat v jakékoli implementaci modelu EDM.  
  
## <a name="entity-type"></a>Typ entity  
 [Typ entity](entity-type.md) je základní stavební blok pro popis struktury dat s model EDM (Entity Data Model). V koncepčním modelu jsou typy entit postavené z [vlastností](property.md) a popisují strukturu konceptů nejvyšší úrovně, jako jsou například zákazníci a objednávky v obchodní aplikaci. Stejným způsobem, že definice třídy v počítačovém programu je šablonou pro instance třídy, je typ entity šablona pro entity. Entita představuje konkrétní objekt (například konkrétního zákazníka nebo objednávky). Každá entita musí mít v [sadě entit](entity-set.md)jedinečný [klíč entity](entity-key.md) .  Sada entit je kolekcí instancí konkrétního typu entity. Sady entit (a [sady přidružení](association-set.md)) jsou logicky seskupeny v [kontejneru entit](entity-container.md).  
  
 Dědičnost je podporována s typy entit: to znamená, že jeden typ entity lze odvodit z jiné třídy. Další informace najdete v tématu [model EDM (Entity Data Model): Dědičnost](entity-data-model-inheritance.md).  
  
## <a name="association-type"></a>Typ přidružení  
 [Typ přidružení](association-type.md) (označovaný také jako asociace) je základní stavební blok pro popis vztahů v model EDM (Entity Data Model). V koncepčním modelu představuje přidružení vztah mezi dvěma typy entit (například zákazník a objednávka). Každé přidružení má dvě [zakončení přidružení](association-end.md) , která určují typy entit zahrnuté do přidružení. Každé zakončení přidružení také určuje [násobnost zakončení přidružení](association-end-multiplicity.md) , která označuje počet entit, které mohou být na tomto konci přidružení. Násobnost zakončení přidružení může mít hodnotu jedna (1), 0 nebo 1 (0.. 1) nebo mnoho (\*). K entitám na jednom konci přidružení lze použít [navigační vlastnosti](navigation-property.md)nebo prostřednictvím cizích klíčů, pokud jsou vystaveny na typu entity. Další informace najdete v tématu [vlastnost cizího klíče](foreign-key-property.md).  
  
 V aplikaci instance přidružení představuje konkrétní přidružení (například přidružení mezi instancí zákazníka a instancemi objednávky). Instance přidružení jsou logicky seskupeny v [sadě přidružení](association-set.md). Sady přidružení (a [sady entit](entity-set.md)) jsou logicky seskupeny v [kontejneru entit](entity-container.md).  
  
## <a name="property"></a>Vlastnost  
 [Typy entit](entity-type.md) obsahují [vlastnosti](property.md) , které definují jejich strukturu a charakteristiky. Například typ entity Zákazník může mít vlastnosti, jako je například KódZákazníka, jméno a adresa.  
  
 Vlastnosti v koncepčním modelu jsou analogické k vlastnostem definovaným ve třídě v počítačovém programu. Stejně jako vlastnosti třídy definují tvar třídy a přenášejí informace o objektech, vlastnosti v koncepčním modelu definují tvar typu entity a přenášejí informace o instancích typu entity.  
  
 Vlastnost může obsahovat primitivní data (například řetězec, celé číslo nebo logickou hodnotu) nebo strukturovaná data (například komplexní typ). Další informace najdete v tématu [model EDM (Entity Data Model): Primitivní datové typy](entity-data-model-primitive-data-types.md).  
  
## <a name="representations-of-a-conceptual-model"></a>Reprezentace koncepčního modelu  
 *Koncepční model* je konkrétní reprezentace struktury některých dat jako entity a vztahy. Jedním ze způsobů, jak znázornit koncepční model, je s diagramem. Následující diagram představuje koncepční model se třemi typy entit (`Book`, `Publisher` `Author`a) a dvěma přidruženími (`PublishedBy` a `WrittenBy`):  
  
 ![Diagram znázorňující koncepční model se třemi typy entit.](./media/entity-data-model-key-concepts/conceptual-model-entity-types-associations.gif)  
  
 Tato reprezentace ale obsahuje několik nedostatků, když k nim dojdou nějaké podrobnosti o modelu. Například typ vlastnosti a informace sady entit nejsou v diagramu předány. Bohatost koncepčního modelu může být od jazyka specifického pro doménu (DSL) výrazně vyjádřena podrobněji. [Entity Framework ADO.NET](./ef/index.md) používá pro definování konceptuálních modelů DSL založenou na jazyce XML s[](./ef/language-reference/csdl-specification.md)názvem *koncepčního jazyka definic (CSDL Schema Definition Language* ). Následuje definice koncepčního modelu v diagramu výše:  
  
 [!code-xml[EDM_Example_Model#EDMExampleCSDL](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#edmexamplecsdl)]  
  
## <a name="see-also"></a>Viz také:

- [Model EDM (Entity Data Model)](entity-data-model.md)
