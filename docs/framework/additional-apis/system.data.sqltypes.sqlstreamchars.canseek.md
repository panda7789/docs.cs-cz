---
title: SqlStreamChars.CanSeek Property (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 52f88a3551e20c74d7a1144c3cd6859a023980db
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/29/2019
ms.locfileid: "58633709"
---
# <a name="sqlstreamcharscanseek-property"></a><span data-ttu-id="841b9-102">SqlStreamChars.CanSeek Property</span><span class="sxs-lookup"><span data-stu-id="841b9-102">SqlStreamChars.CanSeek Property</span></span>

<span data-ttu-id="841b9-103">Při přepisu v odvozené třídě získá hodnotu, která určuje, zda aktuální datový proud podporuje operace seek.</span><span class="sxs-lookup"><span data-stu-id="841b9-103">When overridden in a derived class, gets a value that indicates whether the current steam supports the seek operation.</span></span> <span data-ttu-id="841b9-104">Sestavení, který obsahuje tato vlastnost má relaci typu friend s SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="841b9-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="841b9-105">Je určena pro použití systémem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="841b9-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="841b9-106">U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.</span><span class="sxs-lookup"><span data-stu-id="841b9-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a><span data-ttu-id="841b9-107">Hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="841b9-107">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="841b9-108">`true` Pokud aktuální datový proud podporuje operace seek; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="841b9-108">`true` if the current steam supports the seek operation; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="841b9-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="841b9-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="841b9-110">`SqlStreamChars.CanSeek` Vlastnost je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="841b9-110">The `SqlStreamChars.CanSeek` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="841b9-111">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="841b9-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="841b9-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="841b9-112">Requirements</span></span>

<span data-ttu-id="841b9-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="841b9-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="841b9-114">**Sestavení:** System.Data (v System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="841b9-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="841b9-115">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="841b9-115">**.NET Framework versions:** Available since 2.0.</span></span>