---
title: Model EDM (Entity Data Model) Primitivní datové typy
ms.date: 03/30/2017
ms.assetid: 7635168e-0566-4fdd-8391-7941b0d9f787
ms.openlocfilehash: dd688a06a47f4c44c27ddee2120b9de6980672fc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795156"
---
# <a name="entity-data-model-primitive-data-types"></a>Model EDM (Entity Data Model) Primitivní datové typy
Model EDM (Entity Data Model) (EDM) podporuje sadu abstraktních primitivních datových typů (například String, Boolean, Int32 atd.), které se používají k definování [vlastností](property.md) v koncepčním modelu. Tyto primitivní datové typy jsou proxy pro skutečné primitivní datové typy, které jsou podporovány v úložišti nebo hostitelském prostředí, jako je například databáze SQL Server nebo modul CLR (Common Language Runtime). Model EDM nedefinuje sémantiku operací nebo převody prostřednictvím primitivních datových typů; Tyto sémantiky jsou definovány úložištěm nebo hostitelským prostředím. Základní datové typy v modelu EDM jsou obvykle mapovány na odpovídající primitivní datové typy v úložišti nebo hostitelském prostředí. Informace o tom, jak Entity Framework mapuje primitivní typy v EDM na SQL Server datové typy, najdete v tématu [SqlClient pro Entity Framework](./ef/sqlclient-for-ef-types.md).  
  
> [!NOTE]
> Model EDM nepodporuje kolekce primitivních datových typů.  
  
 Informace o strukturovaných datových typech v modelu EDM naleznete v tématu [typ entity](entity-type.md) a [komplexní typ](complex-type.md).  
  
## <a name="primitive-data-types-supported-in-the-entity-data-model"></a>Primitivní datové typy podporované v model EDM (Entity Data Model)  
 V následující tabulce jsou uvedeny primitivní datové typy, které model EDM podporuje. Tabulka obsahuje také seznam [omezujících vlastností](facet.md) , které lze použít pro každý primitivní datový typ.  
  
|Primitivní datový typ|Popis|Použitelné omezující vlastnosti|  
|-------------------------|-----------------|-----------------------|  
|binární|Obsahuje binární data.|MaxLength, FixedLength, Nullable, default|  
|Boolean|Obsahuje hodnotu `true` nebo `false`.|Nullable, výchozí|  
|Byte|Obsahuje 8bitové celočíselnou hodnotu bez znaménka.|Přesnost, Nullable, výchozí|  
|DateTime|Představuje datum a čas.|Přesnost, Nullable, výchozí|  
|DateTimeOffset|Obsahuje datum a čas jako posun v minutách od času GMT.|Přesnost, Nullable, výchozí|  
|Desetinné číslo|Obsahuje číselnou hodnotu s pevnou přesností a škálováním.|Přesnost, Nullable, výchozí|  
|Double|Obsahuje číslo s plovoucí desetinnou čárkou s 15 číslicemi přesnosti.|Přesnost, Nullable, výchozí|  
|Float|Obsahuje číslo s plovoucí desetinnou čárkou s přesností na sedm číslic.|Přesnost, Nullable, výchozí|  
|Guid|Obsahuje jedinečný identifikátor o velikosti 16 bajtů.|Přesnost, Nullable, výchozí|  
|Int16|Obsahuje 16bitová celočíselnou hodnotu se znaménkem.|Přesnost, Nullable, výchozí|  
|Int32|Obsahuje podepsaná 32 celočíselná hodnota.|Přesnost, Nullable, výchozí|  
|Int64|Obsahuje podepsaná 64 celočíselná hodnota.|Přesnost, Nullable, výchozí|  
|SByte|Obsahuje 8bitové celočíselnou hodnotu se znaménkem.|Přesnost, Nullable, výchozí|  
|String|Obsahuje znaková data.|Unicode, FixedLength, MaxLength, kolace, přesnost, Nullable, default|  
|Time|Obsahuje denní dobu.|Přesnost, Nullable, výchozí|  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)
