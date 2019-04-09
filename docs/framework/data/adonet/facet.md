---
title: omezující vlastnost
ms.date: 03/30/2017
ms.assetid: 91c4e6aa-3e54-4b6c-a38a-abf27808cc85
ms.openlocfilehash: 9353b143a328e0fb183b7870332462a0a2c91b10
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094499"
---
# <a name="facet"></a>omezující vlastnost
A *omezující vlastnost* slouží k přidání podrobností k definici vlastnost primitivního typu. A [vlastnost](../../../../docs/framework/data/adonet/property.md) definice obsahuje informace o typu vlastnosti, ale často je nezbytné další podrobnosti. Typ entity v konceptuálním modelu může mít například vlastnost typu `String` jehož hodnotu nelze nastavit na hodnotu null. Omezující vlastnosti umožňují zadat tato úroveň podrobností.  
  
 Následující tabulka popisuje omezující vlastnosti, které jsou podporovány v modelu EDM.  
  
> [!NOTE]
>  Přesné hodnoty a chování omezujících vlastností jsou určeny běhového prostředí, která používá implementaci modelu EDM.  
  
|omezující vlastnost|Popis|Platí pro|  
|-----------|-----------------|----------------|  
|`Collation`|Určuje pořadí řazení (nebo pořadí řazení) pro použití při provádění porovnání a řazení operací na hodnotách vlastnosti.|`String`|  
|`ConcurrencyMode`|Označuje, že hodnota vlastnosti má být použita pro kontroly optimistické souběžnosti.|Všechny primitivní typ vlastnosti|  
|`Default`|Určuje výchozí hodnotu vlastnosti, pokud není zadána žádná hodnota, při vytváření instance.|Všechny primitivní typ vlastnosti|  
|`FixedLength`|Určuje, zda se může lišit délka hodnoty vlastnosti.|`Binary`,  `String`|  
|`MaxLength`|Určuje maximální délku hodnoty vlastnosti.|`Binary`,  `String`|  
|`Nullable`|Určuje, zda tato vlastnost může mít hodnotu null.|Všechny primitivní typ vlastnosti|  
|`Precision`|Pro vlastnosti typu `Decimal`, určuje počet číslic, může mít hodnotu vlastnosti. Pro vlastnosti typu `Time`, `DateTime`, a `DateTimeOffset`, určuje počet číslic za desetinnou čárkou sady sekund hodnoty vlastnosti.|`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,|  
|`Scale`|Určuje počet číslic vpravo od desetinné čárky pro hodnotu vlastnosti.|Desetinné číslo|  
|`Unicode`|Označuje, zda hodnota vlastnosti je uložen jako kódování Unicode.|`String`|  
  
## <a name="example"></a>Příklad  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů. Definuje následující CSDL `Book` typ entity. Všimněte si, že omezující vlastnosti jsou implementovány jako atributy ve formátu XML. Hodnoty omezujících vlastností, žádná vlastnost definovat jako nastavitelnou hodnotu null a že `Scale` a `Precision` z `Revision` každou vlastnost je nastavena na 29.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
