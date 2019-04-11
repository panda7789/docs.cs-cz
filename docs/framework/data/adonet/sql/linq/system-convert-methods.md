---
title: Metody System.Convert
ms.date: 03/30/2017
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
ms.openlocfilehash: 9836820f2c084a80fcc0a4856f20597716344dfd
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480648"
---
# <a name="systemconvert-methods"></a><span data-ttu-id="09702-102">Metody System.Convert</span><span class="sxs-lookup"><span data-stu-id="09702-102">System.Convert Methods</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="09702-103">nepodporuje následující <xref:System.Convert> metody.</span><span class="sxs-lookup"><span data-stu-id="09702-103">does not support the following <xref:System.Convert> methods.</span></span>

- <span data-ttu-id="09702-104">Verze s využitím <xref:System.IFormatProvider> parametru.</span><span class="sxs-lookup"><span data-stu-id="09702-104">Versions with an <xref:System.IFormatProvider> parameter.</span></span>

- <span data-ttu-id="09702-105">Metody, které se týkají znaková pole nebo pole bajtů:</span><span class="sxs-lookup"><span data-stu-id="09702-105">Methods that involve char arrays or byte arrays:</span></span>

  - <xref:System.Convert.FromBase64CharArray%2A>

  - <xref:System.Convert.ToBase64CharArray%2A>

  - <xref:System.Convert.FromBase64String%2A>

  - <xref:System.Convert.ToBase64String%2A>

- <span data-ttu-id="09702-106">Následující metody:</span><span class="sxs-lookup"><span data-stu-id="09702-106">The following methods:</span></span>

  - `public static <Type2> To<Type2>(<Type1> value);` <span data-ttu-id="09702-107">kde</span><span class="sxs-lookup"><span data-stu-id="09702-107">where</span></span>

    `Type1` <span data-ttu-id="09702-108">a `Type2` jsou jednotlivé `sbyte`, `uint`, `ulong`, nebo `ushort`.</span><span class="sxs-lookup"><span data-stu-id="09702-108">and `Type2` are each one of `sbyte`, `uint`, `ulong`, or `ushort`.</span></span>

  - <span data-ttu-id="09702-109">C#:</span><span class="sxs-lookup"><span data-stu-id="09702-109">C#:</span></span>

    `int To<int type>(string value, int fromBase),`

    `ToString(... value, int toBase)`

  - <span data-ttu-id="09702-110">Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="09702-110">Visual Basic:</span></span>

    `Function To(Of [Numeric])(value as String, fromBase As Integer)`

    `As [Numeric], ToString( value As …, toBase As Integer)`

  - <xref:System.Convert.IsDBNull%2A>

  - <xref:System.Convert.GetTypeCode%2A>

  - <xref:System.Convert.ChangeType%2A>

## <a name="see-also"></a><span data-ttu-id="09702-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="09702-111">See also</span></span>

- [<span data-ttu-id="09702-112">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="09702-112">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
