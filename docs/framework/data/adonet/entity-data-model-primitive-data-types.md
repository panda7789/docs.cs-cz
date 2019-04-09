---
title: Model EDM (Entity Data Model) Primitivní datové typy
ms.date: 03/30/2017
ms.assetid: 7635168e-0566-4fdd-8391-7941b0d9f787
ms.openlocfilehash: 044a0ed981bb9cda3550fb3a3a9f1cb9bff96f25
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142646"
---
# <a name="entity-data-model-primitive-data-types"></a>Model EDM (Entity Data Model) Primitivní datové typy
Entity Data Model (EDM) podporuje sadu abstraktní primitivní datové typy (například řetězce, Boolean, Int32 a tak dále), které se používají k definování [vlastnosti](../../../../docs/framework/data/adonet/property.md) v konceptuálním modelu. Tyto primitivní datové typy jsou proxy servery pro skutečné primitivní datové typy, které jsou podporovány ve službě storage nebo hostitelské prostředí, jako je například do databáze serveru SQL nebo common language runtime (CLR). Modelu EDM primitivní datové typy; nedefinuje sémantiku operací nebo převody Tyto sémantiku jsou definovány úložiště nebo hostitelského prostředí. V modelu EDM primitivní datové typy se obvykle mapují na odpovídající primitivní datové typy ve službě storage nebo hostitelského prostředí. Informace o způsobu, jakým rozhraní Entity Framework mapuje primitivní typy v modelu EDM na datové typy serveru SQL Server najdete v tématu [SqlClient pro typy Entity Framework](../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).  
  
> [!NOTE]
>  Modelu EDM není podporována kolekcí primitivních datových typů.  
  
 Informace o typech strukturovaných dat v modelu EDM najdete v tématu [typ entity](../../../../docs/framework/data/adonet/entity-type.md) a [komplexní typ](../../../../docs/framework/data/adonet/complex-type.md).  
  
## <a name="primitive-data-types-supported-in-the-entity-data-model"></a>Primitivní datové typy podporované v modelu Entity Data Model  
 Následující tabulka uvádí podporované EDM primitivní datové typy. V tabulce jsou také uvedeny [omezující vlastnosti](../../../../docs/framework/data/adonet/facet.md) , který můžete použít pro všechny primitivní datové typy.  
  
|Primitivní datový typ|Popis|Použít omezující vlastnosti|  
|-------------------------|-----------------|-----------------------|  
|binární|Obsahuje binární data.|MaxLength, hodnoty, s možnou hodnotou Null, výchozí|  
|Boolean|Obsahuje hodnotu `true` nebo `false`.|S povolenou hodnotou Null, výchozí|  
|Byte|Obsahuje hodnotu bez znaménka 8bitové celé číslo.|Přesnost, s možnou hodnotou Null, výchozí|  
|DateTime|Představuje datum a čas.|Přesnost, s možnou hodnotou Null, výchozí|  
|DateTimeOffset|Obsahuje data a času jako posun během několika minut od GMT.|Přesnost, s možnou hodnotou Null, výchozí|  
|Desetinné číslo|Obsahuje číselná hodnota s pevnou hodnot precision a scale.|Přesnost, s možnou hodnotou Null, výchozí|  
|Double|Obsahuje plovoucí desetinnou čárkou s přesností na 15 číslic čísla.|Přesnost, s možnou hodnotou Null, výchozí|  
|Float|Obsahuje plovoucí desetinnou čárkou s přesností na sedm číslice čísla.|Přesnost, s možnou hodnotou Null, výchozí|  
|Guid|Obsahuje jedinečný identifikátor 16 bajtů.|Přesnost, s možnou hodnotou Null, výchozí|  
|Int16|Obsahuje hodnotu se znaménkem 16 bitů.|Přesnost, s možnou hodnotou Null, výchozí|  
|Int32|Obsahuje hodnotu se znaménkem 32-bit.|Přesnost, s možnou hodnotou Null, výchozí|  
|Int64|Obsahuje hodnotu se znaménkem 64-bit.|Přesnost, s možnou hodnotou Null, výchozí|  
|SByte|Obsahuje hodnotu se znaménkem 8 bitů.|Přesnost, s možnou hodnotou Null, výchozí|  
|String|Obsahuje znaková data.|Výchozí kódování Unicode, hodnoty, MaxLength, kolace, přesností, s možnou hodnotou Null,|  
|Čas|Obsahuje denní dobu.|Přesnost, s možnou hodnotou Null, výchozí|  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
