---
title: omezující vlastnost
ms.date: 03/30/2017
ms.assetid: 91c4e6aa-3e54-4b6c-a38a-abf27808cc85
ms.openlocfilehash: 2b4a8a559d7297543812f3c67e3b90d06a011b0f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959106"
---
# <a name="facet"></a>omezující vlastnost
*Omezující* vlastnost se používá k přidání podrobností do definice vlastnosti primitivního typu. Definice [vlastnosti](../../../../docs/framework/data/adonet/property.md) obsahuje informace o typu vlastnosti, ale je to často více podrobností. Například typ entity v koncepčním modelu může mít vlastnost typu `String` , jejíž hodnota nemůže být nastavena na hodnotu null. Omezující vlastnosti umožňují zadat tuto úroveň podrobností.  
  
 V následující tabulce jsou popsány omezující vlastnosti, které jsou podporovány v modelu EDM.  
  
> [!NOTE]
> Přesné hodnoty a chování omezujících vlastností jsou určeny prostředím runtime, které používá implementaci modelu EDM.  
  
|Omezující|Popis|Platí pro|  
|-----------|-----------------|----------------|  
|`Collation`|Určuje pořadí kompletování (nebo řazení sekvence), které se má použít při provádění operací porovnání a řazení u hodnot vlastnosti.|`String`|  
|`ConcurrencyMode`|Označuje, že hodnota vlastnosti by měla být použita pro kontroly optimistického řízení souběžnosti.|Vlastnosti všech primitivních typů|  
|`Default`|Určuje výchozí hodnotu vlastnosti, pokud není při vytváření instance zadána žádná hodnota.|Vlastnosti všech primitivních typů|  
|`FixedLength`|Určuje, zda může být délka hodnoty vlastnosti odlišná.|`Binary`, `String`|  
|`MaxLength`|Určuje maximální délku hodnoty vlastnosti.|`Binary`, `String`|  
|`Nullable`|Určuje, zda vlastnost může mít hodnotu null.|Vlastnosti všech primitivních typů|  
|`Precision`|Pro vlastnosti typu `Decimal`určuje počet číslic, které může mít hodnota vlastnosti. Pro vlastnosti typu `Time` `DateTime`,, a `DateTimeOffset`určuje počet číslic pro zlomkovou část hodnoty vlastnosti v sekundách.|`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,|  
|`Scale`|Určuje počet číslic vpravo od desetinné čárky pro hodnotu vlastnosti.|Desetinné číslo|  
|`Unicode`|Určuje, zda je hodnota vlastnosti uložena jako Unicode.|`String`|  
  
## <a name="example"></a>Příklad  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)(konceptuální schéma Definition Language). Následující CSDL definuje `Book` typ entity. Všimněte si, že charakteristiky jsou implementovány jako atributy XML. Hodnoty omezující vlastnosti označují, že žádná vlastnost nemůže být nastavena na hodnotu null a že `Scale` `Revision` vlastnost `Precision` a vlastnosti jsou nastaveny na hodnotu 29.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)
