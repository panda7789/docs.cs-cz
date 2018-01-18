---
title: "omezující vlastnost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91c4e6aa-3e54-4b6c-a38a-abf27808cc85
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 23346fe2095cea2b3f0d705c7d6d8914c35c06f7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="facet"></a>omezující vlastnost
A *omezující vlastnost* se používá k přidání podrobností do definice vlastnost primitivního typu. A [vlastnost](../../../../docs/framework/data/adonet/property.md) definice obsahuje informace o vlastnost typu, ale často je nutné podrobněji. Typ entity v konceptuálním modelu například může mít vlastnost typu `String` jehož hodnota nemůže být nastavena na hodnotu null. Omezující vlastnosti umožňují určit tato úroveň podrobností.  
  
 Následující tabulka popisuje omezující vlastnosti, které jsou podporovány v modelu EDM.  
  
> [!NOTE]
>  Běhové prostředí, která používá implementace EDM určuje přesné hodnoty a chování omezující vlastnosti.  
  
|Omezující vlastnost|Popis|Platí pro|  
|-----------|-----------------|----------------|  
|`Collation`|Určuje pořadí řazení (nebo pořadí řazení) pro použití při provádění porovnání a řazení operací na hodnoty vlastnosti.|`String`|  
|`ConcurrencyMode`|Označuje, že hodnota vlastnosti má být použita pro optimistickou metodu souběžného kontroly.|Všechny vlastnosti primitivní typ|  
|`Default`|Určuje výchozí hodnotu vlastnosti, pokud při vytváření instance je zadána žádná hodnota.|Všechny vlastnosti primitivní typ|  
|`FixedLength`|Určuje, zda se může lišit délka hodnoty vlastnosti.|`Binary`, `String`|  
|`MaxLength`|Určuje maximální délku hodnoty vlastnosti.|`Binary`, `String`|  
|`Nullable`|Určuje, zda vlastnost může mít hodnotu null.|Všechny vlastnosti primitivní typ|  
|`Precision`|Pro vlastnosti typu `Decimal`, určuje počet číslic, může mít hodnotu vlastnosti. Pro vlastnosti typu `Time`, `DateTime`, a `DateTimeOffset`, určuje počet číslic za desetinnou čárkou sekund hodnoty vlastnosti.|`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,|  
|`Scale`|Určuje počet číslic vpravo od desetinné čárky hodnoty vlastnosti.|Desetinné číslo|  
|`Unicode`|Určuje, zda hodnota vlastnosti je uložena ve formátu Unicode.|`String`|  
  
## <a name="example"></a>Příklad  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech. Definuje následující CSDL `Book` typ entity. Všimněte si, že omezující vlastnosti jsou implementované jako atributy XML. Hodnoty omezující vlastnosti udávají, že žádná vlastnost může být nastavena na hodnotu null a který `Scale` a `Precision` z `Revision` každou vlastnost je nastavena na 29.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Viz také  
 [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)
