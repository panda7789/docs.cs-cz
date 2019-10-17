---
title: SqlStreamChars. Seek – Metoda (Int64, SeekOrigin) (System. data. SqlTypes)
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
ms.openlocfilehash: db8aba0a86c140ba62af8056011226532d415951
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395600"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a><span data-ttu-id="0bafb-102">SqlStreamChars. Seek – Metoda (Int64, SeekOrigin)</span><span class="sxs-lookup"><span data-stu-id="0bafb-102">SqlStreamChars.Seek(Int64, SeekOrigin) Method</span></span>

<span data-ttu-id="0bafb-103">Při přepsání v odvozené třídě nastaví pozici v rámci aktuálního datového proudu.</span><span class="sxs-lookup"><span data-stu-id="0bafb-103">When overridden in a derived class, sets the position within the current stream.</span></span> <span data-ttu-id="0bafb-104">Sestavení, které obsahuje tuto metodu, má relaci typu Friend s SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="0bafb-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="0bafb-105">Je určena pro použití v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0bafb-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="0bafb-106">U ostatních databází použijte mechanizmus hostování, který poskytuje tato databáze.</span><span class="sxs-lookup"><span data-stu-id="0bafb-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a><span data-ttu-id="0bafb-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="0bafb-107">Parameters</span></span>

`offset`\
<span data-ttu-id="0bafb-108">Posun bajtů vzhledem k `origin`.</span><span class="sxs-lookup"><span data-stu-id="0bafb-108">A byte offset relative to `origin`.</span></span>

`origin`\
<span data-ttu-id="0bafb-109">Jedna z hodnot výčtu, která určuje referenční bod, z něhož má být získána nová pozice.</span><span class="sxs-lookup"><span data-stu-id="0bafb-109">One of the enumeration values that indicates the reference point from which to obtain the new position.</span></span>

## <a name="returns"></a><span data-ttu-id="0bafb-110">Vrací</span><span class="sxs-lookup"><span data-stu-id="0bafb-110">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="0bafb-111">Nová pozice v aktuálním datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="0bafb-111">The new position within the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="0bafb-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0bafb-112">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="0bafb-113">Metoda `SqlStreamChars.Seek` je soukromá a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="0bafb-113">The `SqlStreamChars.Seek` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="0bafb-114">Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0bafb-114">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="0bafb-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0bafb-115">Requirements</span></span>

<span data-ttu-id="0bafb-116">**Obor názvů:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="0bafb-116">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="0bafb-117">**Sestavení:** System. data (v System. data. dll)</span><span class="sxs-lookup"><span data-stu-id="0bafb-117">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="0bafb-118">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="0bafb-118">**.NET Framework versions:** Available since 2.0.</span></span>
