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
# <a name="type-conversion-tables-in-net"></a><span data-ttu-id="0d9b5-102">Tabulky převodu typů v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="0d9b5-102">Type Conversion Tables in .NET</span></span>
<span data-ttu-id="0d9b5-103">Rozšiřující převod nastane, když hodnota jednoho typu je převedena na jiný typ, který je rovna nebo větší velikosti.</span><span class="sxs-lookup"><span data-stu-id="0d9b5-103">Widening conversion occurs when a value of one type is converted to another type that is of equal or greater size.</span></span> <span data-ttu-id="0d9b5-104">Zužující převod nastane, když hodnota jednoho typu je převést na hodnotu jiného typu, který je menší velikost.</span><span class="sxs-lookup"><span data-stu-id="0d9b5-104">A narrowing conversion occurs when a value of one type is converted to a value of another type that is of a smaller size.</span></span> <span data-ttu-id="0d9b5-105">Tabulky v tomto tématu ilustrují chování vykazují oba typy převody.</span><span class="sxs-lookup"><span data-stu-id="0d9b5-105">The tables in this topic illustrate the behaviors exhibited by both types of conversions.</span></span>  
  
## <a name="widening-conversions"></a><span data-ttu-id="0d9b5-106">Rozšiřující převody</span><span class="sxs-lookup"><span data-stu-id="0d9b5-106">Widening Conversions</span></span>  
 <span data-ttu-id="0d9b5-107">Následující tabulka popisuje rozšiřující převody, které lze provést bez ztráty informací.</span><span class="sxs-lookup"><span data-stu-id="0d9b5-107">The following table describes the widening conversions that can be performed without the loss of information.</span></span>  
  
|<span data-ttu-id="0d9b5-108">Typ</span><span class="sxs-lookup"><span data-stu-id="0d9b5-108">Type</span></span>|<span data-ttu-id="0d9b5-109">Je možné převést bez ztráty dat do</span><span class="sxs-lookup"><span data-stu-id="0d9b5-109">Can be converted without data loss to</span></span>|  
|----------|-------------------------------------------|  
|<xref:System.Byte>|<span data-ttu-id="0d9b5-110"><xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="0d9b5-110"><xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.SByte>|<span data-ttu-id="0d9b5-111"><xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="0d9b5-111"><xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int16>|<span data-ttu-id="0d9b5-112"><xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="0d9b5-112"><xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.UInt16>|<span data-ttu-id="0d9b5-113"><xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="0d9b5-113"><xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Char>|<span data-ttu-id="0d9b5-114"><xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="0d9b5-114"><xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int32>|<span data-ttu-id="0d9b5-115"><xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="0d9b5-115"><xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.UInt32>|<span data-ttu-id="0d9b5-116"><xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="0d9b5-116"><xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int64>|<xref:System.Decimal>|  
|<xref:System.UInt64>|<xref:System.Decimal>|  
|<xref:System.Single>|<xref:System.Double>|  
  
 <span data-ttu-id="0d9b5-117">Některé rozšiřující převody na <xref:System.Single> nebo <xref:System.Double> může způsobit ztrátu přesnosti.</span><span class="sxs-lookup"><span data-stu-id="0d9b5-117">Some widening conversions to <xref:System.Single> or <xref:System.Double> can cause a loss of precision.</span></span> <span data-ttu-id="0d9b5-118">Následující tabulka popisuje rozšiřující převody, které někdy dojít ke ztrátě informací.</span><span class="sxs-lookup"><span data-stu-id="0d9b5-118">The following table describes the widening conversions that sometimes result in a loss of information.</span></span>  
  
|<span data-ttu-id="0d9b5-119">Typ</span><span class="sxs-lookup"><span data-stu-id="0d9b5-119">Type</span></span>|<span data-ttu-id="0d9b5-120">Lze převést na</span><span class="sxs-lookup"><span data-stu-id="0d9b5-120">Can be converted to</span></span>|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<span data-ttu-id="0d9b5-121"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="0d9b5-121"><xref:System.Single>, <xref:System.Double></span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="0d9b5-122"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="0d9b5-122"><xref:System.Single>, <xref:System.Double></span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="0d9b5-123"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="0d9b5-123"><xref:System.Single>, <xref:System.Double></span></span>|  
  
## <a name="narrowing-conversions"></a><span data-ttu-id="0d9b5-124">Zužující převody</span><span class="sxs-lookup"><span data-stu-id="0d9b5-124">Narrowing Conversions</span></span>  
 <span data-ttu-id="0d9b5-125">Zužující převody na <xref:System.Single> nebo <xref:System.Double> může způsobit ztrátu informací.</span><span class="sxs-lookup"><span data-stu-id="0d9b5-125">A narrowing conversion to <xref:System.Single> or <xref:System.Double> can cause a loss of information.</span></span> <span data-ttu-id="0d9b5-126">Pokud cílový typ nemůže správně vyjádřit velikost zdroje, výsledný typ nastaven na konstantu `PositiveInfinity` nebo `NegativeInfinity`.</span><span class="sxs-lookup"><span data-stu-id="0d9b5-126">If the target type cannot properly express the magnitude of the source, the resulting type is set to the constant `PositiveInfinity` or `NegativeInfinity`.</span></span> <span data-ttu-id="0d9b5-127">`PositiveInfinity`Výsledkem dělení nulou kladné číslo a je také vrácena pokud hodnota <xref:System.Single> nebo <xref:System.Double> překračuje hodnotu `MaxValue` pole.</span><span class="sxs-lookup"><span data-stu-id="0d9b5-127">`PositiveInfinity` results from dividing a positive number by zero and is also returned when the value of a <xref:System.Single> or <xref:System.Double> exceeds the value of the `MaxValue` field.</span></span> <span data-ttu-id="0d9b5-128">`NegativeInfinity`Výsledkem dělení nulou záporné číslo a je také vrácena pokud hodnota <xref:System.Single> nebo <xref:System.Double> klesne pod hodnotu `MinValue` pole.</span><span class="sxs-lookup"><span data-stu-id="0d9b5-128">`NegativeInfinity` results from dividing a negative number by zero and is also returned when the value of a <xref:System.Single> or <xref:System.Double> falls below the value of the `MinValue` field.</span></span> <span data-ttu-id="0d9b5-129">Převod z <xref:System.Double> k <xref:System.Single> může mít za následek `PositiveInfinity` nebo `NegativeInfinity`.</span><span class="sxs-lookup"><span data-stu-id="0d9b5-129">A conversion from a <xref:System.Double> to a <xref:System.Single> might result in `PositiveInfinity` or `NegativeInfinity`.</span></span>  
  
 <span data-ttu-id="0d9b5-130">Zužující převod může také způsobit ztrátu informací pro jiné datové typy.</span><span class="sxs-lookup"><span data-stu-id="0d9b5-130">A narrowing conversion can also result in a loss of information for other data types.</span></span> <span data-ttu-id="0d9b5-131">Však <xref:System.OverflowException> je vyvolána, pokud hodnota typu, který je převáděn spadá mimo rozsah určený typ cíle `MaxValue` a `MinValue` pole a převod je ověřen modulem runtime zajistit, aby hodnota cíle typ není větší než jeho `MaxValue` nebo `MinValue`.</span><span class="sxs-lookup"><span data-stu-id="0d9b5-131">However, an <xref:System.OverflowException> is thrown if the value of a type that is being converted falls outside of the range specified by the target type's `MaxValue` and `MinValue` fields, and the conversion is checked by the runtime to ensure that the value of the target type does not exceed its `MaxValue` or `MinValue`.</span></span> <span data-ttu-id="0d9b5-132">Převody, které se provádí pomocí <xref:System.Convert?displayProperty=nameWithType> třídy jsou vždy zaškrtnuto tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="0d9b5-132">Conversions that are performed with the <xref:System.Convert?displayProperty=nameWithType> class are always checked in this manner.</span></span>  
  
 <span data-ttu-id="0d9b5-133">Následující tabulka uvádí převody, které vyvolají <xref:System.OverflowException> pomocí <xref:System.Convert?displayProperty=nameWithType> nebo kterákoli zaškrtnutá převodu, pokud je hodnota typu převáděné mimo definovaný rozsah výsledného typu.</span><span class="sxs-lookup"><span data-stu-id="0d9b5-133">The following table lists conversions that throw an <xref:System.OverflowException> using <xref:System.Convert?displayProperty=nameWithType> or any checked conversion if the value of the type being converted is outside the defined range of the resulting type.</span></span>  
  
|<span data-ttu-id="0d9b5-134">Typ</span><span class="sxs-lookup"><span data-stu-id="0d9b5-134">Type</span></span>|<span data-ttu-id="0d9b5-135">Lze převést na</span><span class="sxs-lookup"><span data-stu-id="0d9b5-135">Can be converted to</span></span>|  
|----------|-------------------------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<span data-ttu-id="0d9b5-136"><xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="0d9b5-136"><xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64></span></span>|  
|<xref:System.Int16>|<span data-ttu-id="0d9b5-137"><xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16></span><span class="sxs-lookup"><span data-stu-id="0d9b5-137"><xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16></span></span>|  
|<xref:System.UInt16>|<span data-ttu-id="0d9b5-138"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16></span><span class="sxs-lookup"><span data-stu-id="0d9b5-138"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16></span></span>|  
|<xref:System.Int32>|<span data-ttu-id="0d9b5-139"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32></span><span class="sxs-lookup"><span data-stu-id="0d9b5-139"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32></span></span>|  
|<xref:System.UInt32>|<span data-ttu-id="0d9b5-140"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="0d9b5-140"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32></span></span>|  
|<xref:System.Int64>|<span data-ttu-id="0d9b5-141"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="0d9b5-141"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64></span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="0d9b5-142"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64></span><span class="sxs-lookup"><span data-stu-id="0d9b5-142"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64></span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="0d9b5-143"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="0d9b5-143"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
|<xref:System.Single>|<span data-ttu-id="0d9b5-144"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="0d9b5-144"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
|<xref:System.Double>|<span data-ttu-id="0d9b5-145"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="0d9b5-145"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0d9b5-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d9b5-146">See Also</span></span>  
 <xref:System.Convert?displayProperty=nameWithType>  
 [<span data-ttu-id="0d9b5-147">Převod typů v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="0d9b5-147">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)
