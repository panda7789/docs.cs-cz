---
title: Metoda SqlStreamChars.Dispose(Boolean) (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Dispose
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: cc8df68a608000d89dd322b0d396504483bbf372
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/29/2019
ms.locfileid: "58633722"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a><span data-ttu-id="9c0a7-102">SqlStreamChars.Dispose(Boolean) – metoda</span><span class="sxs-lookup"><span data-stu-id="9c0a7-102">SqlStreamChars.Dispose(Boolean) Method</span></span>

<span data-ttu-id="9c0a7-103">Při přepisu v odvozené třídě, uvolní prostředky využívané třídou datového proudu.</span><span class="sxs-lookup"><span data-stu-id="9c0a7-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="9c0a7-104">Sestavení, který obsahuje tato metoda má relaci typu friend s SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="9c0a7-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="9c0a7-105">Je určena pro použití systémem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9c0a7-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="9c0a7-106">U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.</span><span class="sxs-lookup"><span data-stu-id="9c0a7-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a><span data-ttu-id="9c0a7-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c0a7-107">Parameters</span></span>

`disposing`\
<span data-ttu-id="9c0a7-108">`true` k uvolnění spravovaných i nespravovaných prostředků; `false` k uvolnění pouze nespravovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="9c0a7-108">`true` to release both managed and unmanaged resources; `false` to release only unmanaged resources.</span></span>

## <a name="remarks"></a><span data-ttu-id="9c0a7-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9c0a7-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="9c0a7-110">`SqlStreamChars.Dispose` Metoda je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="9c0a7-110">The `SqlStreamChars.Dispose` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="9c0a7-111">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="9c0a7-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="9c0a7-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9c0a7-112">Requirements</span></span>

<span data-ttu-id="9c0a7-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="9c0a7-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="9c0a7-114">**Sestavení:** System.Data (v System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="9c0a7-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="9c0a7-115">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="9c0a7-115">**.NET Framework versions:** Available since 2.0.</span></span>