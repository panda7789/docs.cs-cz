---
title: "Tabulky převodu typů v rozhraní .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e741de47fec5f0ed607bba33b963d449c5c51cce
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="type-conversion-tables-in-net"></a>Tabulky převodu typů v rozhraní .NET
Rozšiřující převod nastane, když hodnota jednoho typu je převedena na jiný typ, který je rovna nebo větší velikosti. Zužující převod nastane, když hodnota jednoho typu je převést na hodnotu jiného typu, který je menší velikost. Tabulky v tomto tématu ilustrují chování vykazují oba typy převody.  
  
## <a name="widening-conversions"></a>Rozšiřující převody  
 Následující tabulka popisuje rozšiřující převody, které lze provést bez ztráty informací.  
  
|Typ|Je možné převést bez ztráty dat do|  
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
  
|Typ|Lze převést na|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## <a name="narrowing-conversions"></a>Zužující převody  
 Zužující převody na <xref:System.Single> nebo <xref:System.Double> může způsobit ztrátu informací. Pokud cílový typ nemůže správně vyjádřit velikost zdroje, výsledný typ nastaven na konstantu `PositiveInfinity` nebo `NegativeInfinity`. `PositiveInfinity`Výsledkem dělení nulou kladné číslo a je také vrácena pokud hodnota <xref:System.Single> nebo <xref:System.Double> překračuje hodnotu `MaxValue` pole. `NegativeInfinity`Výsledkem dělení nulou záporné číslo a je také vrácena pokud hodnota <xref:System.Single> nebo <xref:System.Double> klesne pod hodnotu `MinValue` pole. Převod z <xref:System.Double> k <xref:System.Single> může mít za následek `PositiveInfinity` nebo `NegativeInfinity`.  
  
 Zužující převod může také způsobit ztrátu informací pro jiné datové typy. Však <xref:System.OverflowException> je vyvolána, pokud hodnota typu, který je převáděn spadá mimo rozsah určený typ cíle `MaxValue` a `MinValue` pole a převod je ověřen modulem runtime zajistit, aby hodnota cíle typ není větší než jeho `MaxValue` nebo `MinValue`. Převody, které se provádí pomocí <xref:System.Convert?displayProperty=nameWithType> třídy jsou vždy zaškrtnuto tímto způsobem.  
  
 Následující tabulka uvádí převody, které vyvolají <xref:System.OverflowException> pomocí <xref:System.Convert?displayProperty=nameWithType> nebo kterákoli zaškrtnutá převodu, pokud je hodnota typu převáděné mimo definovaný rozsah výsledného typu.  
  
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
 <xref:System.Convert?displayProperty=nameWithType>  
 [Převod typů v rozhraní .NET](../../../docs/standard/base-types/type-conversion.md)
