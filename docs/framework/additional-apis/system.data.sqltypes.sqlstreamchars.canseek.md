---
title: Vlastnost SqlStreamChars.CanSeek (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 0145fe87e2c8aa3dd40e73f0089fe40b6b6cca30
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152239"
---
# <a name="sqlstreamcharscanseek-property"></a><span data-ttu-id="cc4c5-102">Vlastnost SqlStreamChars.CanSeek</span><span class="sxs-lookup"><span data-stu-id="cc4c5-102">SqlStreamChars.CanSeek Property</span></span>

<span data-ttu-id="cc4c5-103">Při přepisu v odvozené třídě získá hodnotu, která určuje, zda aktuální datový proud podporuje operace seek.</span><span class="sxs-lookup"><span data-stu-id="cc4c5-103">When overridden in a derived class, gets a value that indicates whether the current steam supports the seek operation.</span></span> <span data-ttu-id="cc4c5-104">Sestavení, který obsahuje tato vlastnost má relaci typu friend s SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="cc4c5-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="cc4c5-105">Je určena pro použití systémem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cc4c5-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="cc4c5-106">U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.</span><span class="sxs-lookup"><span data-stu-id="cc4c5-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a><span data-ttu-id="cc4c5-107">Hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="cc4c5-107">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="cc4c5-108">`true` Pokud aktuální datový proud podporuje operace seek; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="cc4c5-108">`true` if the current steam supports the seek operation; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="cc4c5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cc4c5-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="cc4c5-110">`SqlStreamChars.CanSeek` Vlastnost je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="cc4c5-110">The `SqlStreamChars.CanSeek` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="cc4c5-111">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="cc4c5-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="cc4c5-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc4c5-112">Requirements</span></span>

<span data-ttu-id="cc4c5-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="cc4c5-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="cc4c5-114">**Sestavení:** System.Data (v System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="cc4c5-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="cc4c5-115">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="cc4c5-115">**.NET Framework versions:** Available since 2.0.</span></span>