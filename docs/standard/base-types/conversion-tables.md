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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73103892"
---
# <a name="type-conversion-tables-in-net"></a>Tabulky převodu typů v .NET
Rozšiřující převod nastane, když je hodnota jednoho typu převedena na jiný typ, který má stejnou nebo větší velikost. Zužující převod dochází při převedení hodnoty jednoho typu na hodnotu jiného typu, který je menší velikosti. Tabulky v tomto tématu ilustrují chování vystavované oběma typy převodů.  
  
## <a name="widening-conversions"></a>Rozšíření převodů  
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
  
 Některé rozšiřující převody <xref:System.Single> <xref:System.Double> nebo může způsobit ztrátu přesnosti. Následující tabulka popisuje rozšiřující převody, které někdy vedou ke ztrátě informací.  
  
|Typ|Lze převést na|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## <a name="narrowing-conversions"></a>Zužující převody  
 Zužující převod <xref:System.Single> <xref:System.Double> na nebo může způsobit ztrátu informací. Pokud cílový typ nemůže správně vyjádřit velikost zdroje, výsledný typ je `PositiveInfinity` `NegativeInfinity`nastaven na konstantu nebo . `PositiveInfinity`vyděleníkladného čísla nulou a je také <xref:System.Single> vráceno, když hodnota nebo <xref:System.Double> vyšší hodnota `MaxValue` pole. `NegativeInfinity`vyplývá z dělení záporného čísla nulou a <xref:System.Single> <xref:System.Double> je také vrácena, když hodnota nebo klesne pod hodnotu `MinValue` pole. Převod z <xref:System.Double> a <xref:System.Single> na může `PositiveInfinity` `NegativeInfinity`mít za následek nebo .  
  
 Zužující převod může také způsobit ztrátu informací pro jiné datové typy. Je však vyvolána, pokud hodnota <xref:System.OverflowException> typu, který je převáděn spadá `MaxValue` mimo `MinValue` rozsah určený cílový typ a pole a převod je kontrolována za běhu, aby bylo zajištěno, že hodnota cílového typu nepřesahuje jeho `MaxValue` nebo `MinValue`. Převody, které jsou <xref:System.Convert?displayProperty=nameWithType> prováděny s třídou jsou vždy kontrolovány tímto způsobem.  
  
 V následující tabulce jsou uvedeny převody, které vyvolány <xref:System.OverflowException> using <xref:System.Convert?displayProperty=nameWithType> nebo jakýkoli kontrolovaný převod, pokud je hodnota převáděného typu mimo definovaný rozsah výsledného typu.  
  
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
- [Převod typů v rozhraní .NET](../../../docs/standard/base-types/type-conversion.md)
