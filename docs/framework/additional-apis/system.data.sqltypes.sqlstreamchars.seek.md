---
title: Metoda SqlStreamChars.Seek (Int64, SeekOrigin) (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 6b69f87da9fb3829d765dc135de1f6c10765b63a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634363"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a><span data-ttu-id="fc9bc-102">Metoda SqlStreamChars.Seek (Int64, SeekOrigin)</span><span class="sxs-lookup"><span data-stu-id="fc9bc-102">SqlStreamChars.Seek(Int64, SeekOrigin) Method</span></span>

<span data-ttu-id="fc9bc-103">Při přepisu v odvozené třídě, nastaví pozici v rámci aktuální datový proud.</span><span class="sxs-lookup"><span data-stu-id="fc9bc-103">When overridden in a derived class, sets the position within the current stream.</span></span> <span data-ttu-id="fc9bc-104">Sestavení, který obsahuje tato metoda má relaci typu friend s SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="fc9bc-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="fc9bc-105">Je určena pro použití systémem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fc9bc-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="fc9bc-106">U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.</span><span class="sxs-lookup"><span data-stu-id="fc9bc-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a><span data-ttu-id="fc9bc-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc9bc-107">Parameters</span></span>

`offset`\
<span data-ttu-id="fc9bc-108">Posun bajtů vzhledem k `origin`.</span><span class="sxs-lookup"><span data-stu-id="fc9bc-108">A byte offset relative to `origin`.</span></span>

`origin`\
<span data-ttu-id="fc9bc-109">Jedna z hodnot výčtu, které určuje referenční bod, ze kterého chcete získat nové pozice.</span><span class="sxs-lookup"><span data-stu-id="fc9bc-109">One of the enumeration values that indicates the reference point from which to obtain the new position.</span></span>

## <a name="returns"></a><span data-ttu-id="fc9bc-110">Vrací</span><span class="sxs-lookup"><span data-stu-id="fc9bc-110">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="fc9bc-111">Novou pozici v rámci aktuální datový proud.</span><span class="sxs-lookup"><span data-stu-id="fc9bc-111">The new position within the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="fc9bc-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc9bc-112">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="fc9bc-113">`SqlStreamChars.Seek` Metoda je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="fc9bc-113">The `SqlStreamChars.Seek` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="fc9bc-114">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="fc9bc-114">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="fc9bc-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc9bc-115">Requirements</span></span>

<span data-ttu-id="fc9bc-116">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="fc9bc-116">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="fc9bc-117">**Sestavení:** System.Data (v System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="fc9bc-117">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="fc9bc-118">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="fc9bc-118">**.NET Framework versions:** Available since 2.0.</span></span>
