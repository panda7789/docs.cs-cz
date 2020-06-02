---
title: Tabulky převodu typů v .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- widening conversions
- narrowing conversions
- type conversion, table
- converting types, narrowing conversions
- converting types, widening conversions
- base types, converting
- tables [.NET Framework], type conversions
- data types [.NET Framework], converting
ms.assetid: 0ea65c59-85eb-4a52-94ca-c36d3bd13058
ms.openlocfilehash: bb696c65078a5dae0b81a48bffc786d2257496c3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290562"
---
# <a name="type-conversion-tables-in-net"></a>Tabulky převodu typů v .NET
Rozšiřující převod nastane, pokud je hodnota jednoho typu převedena na jiný typ, který má stejnou nebo větší velikost. Zužující převod nastane, pokud je hodnota jednoho typu převedena na hodnotu jiného typu, který má menší velikost. Tabulky v tomto tématu ilustrují chování, které se projeví v obou typech převodů.  
  
## <a name="widening-conversions"></a>Rozšiřující převody  
 Následující tabulka popisuje rozšiřující převody, které lze provést bez ztráty informací.  
  
|Typ|Lze převést bez ztráty dat na|  
|----------|-------------------------------------------|  
|<xref:System.Byte>|<xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.SByte>|<xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int16>|<xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt16>|<xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Char>|<xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int32>|<xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt32>|<xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int64>|<xref:System.Decimal>|  
|<xref:System.UInt64>|<xref:System.Decimal>|  
|<xref:System.Single>|<xref:System.Double>|  
  
 Některé rozšiřující převody na <xref:System.Single> nebo <xref:System.Double> mohou způsobit ztrátu přesnosti. Následující tabulka popisuje rozšiřující převody, které někdy vedou ke ztrátě informací.  
  
|Typ|Lze převést na|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## <a name="narrowing-conversions"></a>Zužující převody  
 Zužující převod na <xref:System.Single> nebo <xref:System.Double> může způsobit ztrátu informací. Pokud cílový typ nemůže správně vyjadřovat velikost zdroje, výsledný typ je nastaven na konstantu `PositiveInfinity` nebo `NegativeInfinity` . `PositiveInfinity`je výsledkem dělení kladného čísla nulou a je také vráceno, pokud hodnota <xref:System.Single> nebo <xref:System.Double> překročí hodnotu `MaxValue` pole. `NegativeInfinity`je výsledkem dělení záporného čísla nulou a je také vráceno, pokud hodnota <xref:System.Single> nebo <xref:System.Double> spadá pod hodnotu `MinValue` pole. Převod z typu <xref:System.Double> na a <xref:System.Single> může mít za následek `PositiveInfinity` nebo `NegativeInfinity` .  
  
 Zužující převod může také vést ke ztrátě informací pro jiné datové typy. <xref:System.OverflowException>Je-li však vyvolána hodnota převáděného typu, nespadají mimo rozsah určený cílovým typem `MaxValue` a polem a `MinValue` Převod je zkontrolován modulem runtime, aby bylo zajištěno, že hodnota cílového typu nepřekračuje hodnotu `MaxValue` nebo `MinValue` . Převody, které jsou provedeny s <xref:System.Convert?displayProperty=nameWithType> třídou, jsou vždy tímto způsobem kontrolovány.  
  
 V následující tabulce je uveden seznam převodů, které vyvolávají <xref:System.OverflowException> použití <xref:System.Convert?displayProperty=nameWithType> nebo libovolný kontrolovaný převod, pokud hodnota převáděného typu je mimo definovaný rozsah výsledného typu.  
  
|Typ|Lze převést na|  
|----------|-------------------------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>|  
|<xref:System.Int16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16>|  
|<xref:System.UInt16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>|  
|<xref:System.Int32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32>|  
|<xref:System.UInt32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>|  
|<xref:System.Int64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64>|  
|<xref:System.UInt64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>|  
|<xref:System.Decimal>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Single>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Double>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Convert?displayProperty=nameWithType>
- [Převod typu v .NET](type-conversion.md)
