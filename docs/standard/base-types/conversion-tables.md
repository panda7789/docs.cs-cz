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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f018ed182e6354bbc6e6873f0df1b35e023c9c17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650320"
---
# <a name="type-conversion-tables-in-net"></a>Tabulky převodu typů v .NET
Rozšiřující převod vyvolá při převodu hodnoty jednoho typu na jiný typ, který je roven nebo větší velikosti. Zužující převod nastane, pokud je hodnota jednoho typu je převedena na hodnotu jiný typ, který je menší velikost. Tabulky v tomto tématu ilustrují chování vykazují oba typy převodů.  
  
## <a name="widening-conversions"></a>Rozšiřující převody  
 Následující tabulka popisuje rozšiřující převody, které lze provést bez ztráty informací.  
  
|Type|Je možné převést bez ztráty dat do|  
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
  
 Některé rozšiřující převody na <xref:System.Single> nebo <xref:System.Double> může způsobit ztrátu přesnosti. Následující tabulka popisuje rozšiřující převody, které někdy dojít ke ztrátě informací.  
  
|Type|Je možné převést na|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## <a name="narrowing-conversions"></a>Zužující převody  
 Zužující převody na <xref:System.Single> nebo <xref:System.Double> může způsobit ztrátu informací. Pokud cílový typ nelze vyjádřit správně velikost zdroje, výsledný typ je nastaven na konstantu `PositiveInfinity` nebo `NegativeInfinity`. `PositiveInfinity` Výsledkem dělení nulou kladné číslo a je také vrácen při hodnotu <xref:System.Single> nebo <xref:System.Double> překračuje hodnotu `MaxValue` pole. `NegativeInfinity` Výsledkem dělení zápornou nulou a je také vrácen při hodnotu <xref:System.Single> nebo <xref:System.Double> klesne pod hodnotu `MinValue` pole. Převod z <xref:System.Double> k <xref:System.Single> může mít za následek `PositiveInfinity` nebo `NegativeInfinity`.  
  
 Zužující převod může také vést ke ztrátě informací pro jiné datové typy. Nicméně <xref:System.OverflowException> je vyvolána, pokud hodnota typu, který je převáděn spadá mimo rozsah určený cílový typ `MaxValue` a `MinValue` pole a převod je zaškrtnuté políčko modulem runtime a zkontrolujte, že hodnota cíle typ není delší než jeho `MaxValue` nebo `MinValue`. Převody, které se pomocí provádí <xref:System.Convert?displayProperty=nameWithType> třídy je vždy zaškrtnuto tímto způsobem.  
  
 V následující tabulce jsou uvedeny převody, které vyvolají <xref:System.OverflowException> pomocí <xref:System.Convert?displayProperty=nameWithType> nebo pokud hodnota převáděného typu je mimo definovaný rozsah výsledný typ kterákoli zaškrtnutá převodu.  
  
|Type|Je možné převést na|  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Convert?displayProperty=nameWithType>
- [Převod typů v rozhraní .NET](../../../docs/standard/base-types/type-conversion.md)
