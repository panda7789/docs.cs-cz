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
ms.openlocfilehash: aa1ef8397338af949bd147fd3252b2d9ecaf53ef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103892"
---
# <a name="type-conversion-tables-in-net"></a>Tabulky převodu typů v .NET
Rozšiřující převod nastane, pokud je hodnota jednoho typu převedena na jiný typ, který má stejnou nebo větší velikost. Zužující převod nastane, pokud je hodnota jednoho typu převedena na hodnotu jiného typu, který má menší velikost. Tabulky v tomto tématu ilustrují chování, které se projeví v obou typech převodů.  
  
## <a name="widening-conversions"></a>Rozšiřující převody  
 Následující tabulka popisuje rozšiřující převody, které lze provést bez ztráty informací.  
  
|Typ|Lze převést bez ztráty dat na|  
|----------|-------------------------------------------|  
|<xref:System.Byte>|<xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.SByte>|<xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double><xref:System.Decimal>|  
|<xref:System.Int16>|<xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double><xref:System.Decimal>|  
|<xref:System.UInt16>|<xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Char>|<xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int32>|<xref:System.Int64>, <xref:System.Double><xref:System.Decimal>|  
|<xref:System.UInt32>|<xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double><xref:System.Decimal>|  
|<xref:System.Int64>|<xref:System.Decimal>|  
|<xref:System.UInt64>|<xref:System.Decimal>|  
|<xref:System.Single>|<xref:System.Double>|  
  
 Některé rozšiřující převody na <xref:System.Single> nebo <xref:System.Double> mohou způsobit ztrátu přesnosti. Následující tabulka popisuje rozšiřující převody, které někdy vedou ke ztrátě informací.  
  
|Typ|Lze převést na|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single><xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single><xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single><xref:System.Double>|  
  
## <a name="narrowing-conversions"></a>Zužující převody  
 Zužující převod na <xref:System.Single> nebo <xref:System.Double> může způsobit ztrátu informací. Pokud cílový typ nemůže správně vyjadřovat velikost zdroje, výsledný typ je nastaven na konstantu `PositiveInfinity` nebo `NegativeInfinity`. `PositiveInfinity` je výsledkem dělení kladného čísla nulou a je vrácena také v případě, že hodnota <xref:System.Single> nebo <xref:System.Double> překračuje hodnotu pole `MaxValue`. `NegativeInfinity` je výsledkem dělení záporného čísla nulou a je vráceno také v případě, že hodnota <xref:System.Single> nebo <xref:System.Double> klesne pod hodnotu pole `MinValue`. Převod z <xref:System.Double> na <xref:System.Single> může mít za následek `PositiveInfinity` nebo `NegativeInfinity`.  
  
 Zužující převod může také vést ke ztrátě informací pro jiné datové typy. <xref:System.OverflowException> je však vyvolána, pokud hodnota převáděného typu spadá mimo rozsah určený `MaxValue` a `MinValue` polích cílového typu a převod je zkontrolován modulem runtime, aby bylo zajištěno, že hodnota cílového typu nepřekračuje hodnotu. jeho `MaxValue` nebo `MinValue`. Převody, které jsou prováděny pomocí třídy <xref:System.Convert?displayProperty=nameWithType>, jsou tímto způsobem vždy kontrolovány.  
  
 V následující tabulce je uveden seznam převodů, které vyvolávají <xref:System.OverflowException> pomocí <xref:System.Convert?displayProperty=nameWithType> nebo jakýkoli kontrolovaný převod, pokud hodnota převáděného typu je mimo definovaný rozsah výsledného typu.  
  
|Typ|Lze převést na|  
|----------|-------------------------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32><xref:System.UInt64>|  
|<xref:System.Int16>|<xref:System.Byte>, <xref:System.SByte><xref:System.UInt16>|  
|<xref:System.UInt16>|<xref:System.Byte>, <xref:System.SByte><xref:System.Int16>|  
|<xref:System.Int32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16><xref:System.UInt32>|  
|<xref:System.UInt32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16><xref:System.Int32>|  
|<xref:System.Int64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64>|  
|<xref:System.UInt64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>|  
|<xref:System.Decimal>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Single>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Double>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Convert?displayProperty=nameWithType>
- [Převod typů v rozhraní .NET](../../../docs/standard/base-types/type-conversion.md)
