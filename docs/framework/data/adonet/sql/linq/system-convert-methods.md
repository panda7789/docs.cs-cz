---
title: Metody System.Convert
ms.date: 03/30/2017
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
ms.openlocfilehash: d0aa0b11223e23b874471962d727d8e16e152ceb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781058"
---
# <a name="systemconvert-methods"></a><span data-ttu-id="56518-102">Metody System.Convert</span><span class="sxs-lookup"><span data-stu-id="56518-102">System.Convert Methods</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="56518-103">nepodporuje následující <xref:System.Convert> metody.</span><span class="sxs-lookup"><span data-stu-id="56518-103">does not support the following <xref:System.Convert> methods.</span></span>

- <span data-ttu-id="56518-104">Verze s <xref:System.IFormatProvider> parametrem.</span><span class="sxs-lookup"><span data-stu-id="56518-104">Versions with an <xref:System.IFormatProvider> parameter.</span></span>

- <span data-ttu-id="56518-105">Metody, které zahrnují pole znaků nebo Bajtová pole:</span><span class="sxs-lookup"><span data-stu-id="56518-105">Methods that involve char arrays or byte arrays:</span></span>

  - <xref:System.Convert.FromBase64CharArray%2A>

  - <xref:System.Convert.ToBase64CharArray%2A>

  - <xref:System.Convert.FromBase64String%2A>

  - <xref:System.Convert.ToBase64String%2A>

- <span data-ttu-id="56518-106">Následující metody:</span><span class="sxs-lookup"><span data-stu-id="56518-106">The following methods:</span></span>

  - <span data-ttu-id="56518-107">`public static <Type2> To<Type2>(<Type1> value);`,</span><span class="sxs-lookup"><span data-stu-id="56518-107">`public static <Type2> To<Type2>(<Type1> value);` where</span></span>

    <span data-ttu-id="56518-108">`Type1`a `Type2` jsou každý z `sbyte`nich, `uint`, `ulong`nebo. `ushort`</span><span class="sxs-lookup"><span data-stu-id="56518-108">`Type1` and `Type2` are each one of `sbyte`, `uint`, `ulong`, or `ushort`.</span></span>

  - <span data-ttu-id="56518-109">C#:</span><span class="sxs-lookup"><span data-stu-id="56518-109">C#:</span></span>

    `int To<int type>(string value, int fromBase),`

    `ToString(... value, int toBase)`

  - <span data-ttu-id="56518-110">Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="56518-110">Visual Basic:</span></span>

    `Function To(Of [Numeric])(value as String, fromBase As Integer)`

    `As [Numeric], ToString( value As …, toBase As Integer)`

  - <xref:System.Convert.IsDBNull%2A>

  - <xref:System.Convert.GetTypeCode%2A>

  - <xref:System.Convert.ChangeType%2A>

## <a name="see-also"></a><span data-ttu-id="56518-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56518-111">See also</span></span>

- [<span data-ttu-id="56518-112">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="56518-112">Data Types and Functions</span></span>](data-types-and-functions.md)
