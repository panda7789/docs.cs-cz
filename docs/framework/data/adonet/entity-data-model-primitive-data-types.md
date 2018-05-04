---
title: 'Datového modelu entity: Primitivní datové typy'
ms.date: 03/30/2017
ms.assetid: 7635168e-0566-4fdd-8391-7941b0d9f787
ms.openlocfilehash: 3e99f65c57cf0e0ee4cbccc79d5819d39b9ee60b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="entity-data-model-primitive-data-types"></a>Datového modelu entity: Primitivní datové typy
Entity Data Model (EDM) podporuje sadu abstraktní primitivní datové typy (například řetězec, logická hodnota, Int32 a tak dále), které se používají k definování [vlastnosti](../../../../docs/framework/data/adonet/property.md) v konceptuálním modelu. Tyto primitivní datové typy jsou proxy pro skutečné primitivní datové typy, které jsou podporovány v úložiště nebo hostování prostředí, například do databáze SQL serveru nebo modul CLR (CLR). EDM nedefinuje sémantika operace nebo převody přes primitivní datové typy; Tyto sémantiku jsou definovány úložiště nebo hostitelské prostředí. Primitivní datové typy v modelu EDM obvykle, jsou namapované na odpovídající primitivní datové typy úložiště nebo hostitelské prostředí. Informace o tom, jak rozhraní Entity Framework mapuje primitivní typy v modelu EDM datové typy systému SQL Server najdete v tématu [SqlClient pro Entity FrameworkTypes](../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).  
  
> [!NOTE]
>  EDM nepodporuje kolekce primitivní datové typy.  
  
 Informace o typech strukturovaných dat v modelu EDM najdete v tématu [typ entity](../../../../docs/framework/data/adonet/entity-type.md) a [komplexní typ](../../../../docs/framework/data/adonet/complex-type.md).  
  
## <a name="primitive-data-types-supported-in-the-entity-data-model"></a>Primitivní datové typy podporované v datovém modelu Entity  
 Následující tabulka uvádí nepodporuje EDM primitivní datové typy. Jsou zde také uvedeny [omezující vlastnosti](../../../../docs/framework/data/adonet/facet.md) který lze použít pro jednotlivé primitivní datové typy.  
  
|Primitivní datový typ|Popis|Použít omezující vlastnosti|  
|-------------------------|-----------------|-----------------------|  
|binární|Obsahuje binární data.|MaxLength řetězci FixedLength, s možnou hodnotou Null, výchozí|  
|Boolean|Obsahuje hodnotu `true` nebo `false`.|S možnou hodnotou Null, výchozí|  
|Byte|Obsahuje hodnotu nepodepsané 8bitové celé číslo.|Přesnost, s možnou hodnotou Null, výchozí|  
|DateTime|Představuje datum a čas.|Přesnost, s možnou hodnotou Null, výchozí|  
|DateTimeOffset|Obsahuje datum a čas jako posun v minutách od GMT.|Přesnost, s možnou hodnotou Null, výchozí|  
|Desetinné číslo|Obsahuje číselnou hodnotu s pevnou přesnost a měřítko.|Přesnost, s možnou hodnotou Null, výchozí|  
|Double|Obsahuje bod plovoucí desetinné číslo s přesností na 15 číslic.|Přesnost, s možnou hodnotou Null, výchozí|  
|Plovoucí desetinná čárka|Obsahuje bod plovoucí desetinné číslo s přesností sedm číslic.|Přesnost, s možnou hodnotou Null, výchozí|  
|Identifikátor GUID|Obsahuje jedinečný identifikátor 16 bajtů.|Přesnost, s možnou hodnotou Null, výchozí|  
|Int16|Obsahuje hodnotu podepsaný 16bitové celé číslo.|Přesnost, s možnou hodnotou Null, výchozí|  
|Int32|Obsahuje hodnotu podepsaný 32bitové celé číslo.|Přesnost, s možnou hodnotou Null, výchozí|  
|Int64|Obsahuje hodnotu podepsaný 64bitové celé číslo.|Přesnost, s možnou hodnotou Null, výchozí|  
|SByte|Obsahuje hodnotu podepsaný 8bitové celé číslo.|Přesnost, s možnou hodnotou Null, výchozí|  
|String|Obsahuje znak data.|Znakové sady Unicode, FixedLength, MaxLength, kolace, přesnost, s možnou hodnotou Null, výchozí|  
|Čas|Obsahuje denní doby.|Přesnost, s možnou hodnotou Null, výchozí|  
  
## <a name="see-also"></a>Viz také  
 [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)
