---
title: SqlStreamChars. Dispose (Boolean) – metoda (System. data. SqlTypes)
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
ms.openlocfilehash: 44dc97835b8a7141064e8de4d2d5325c40be5a34
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395757"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a><span data-ttu-id="b6c6e-102">SqlStreamChars. Dispose (Boolean) – metoda</span><span class="sxs-lookup"><span data-stu-id="b6c6e-102">SqlStreamChars.Dispose(Boolean) Method</span></span>

<span data-ttu-id="b6c6e-103">Při přepsání v odvozené třídě uvolní prostředky používané datovým proudem.</span><span class="sxs-lookup"><span data-stu-id="b6c6e-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="b6c6e-104">Sestavení, které obsahuje tuto metodu, má relaci typu Friend s SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="b6c6e-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="b6c6e-105">Je určena pro použití v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b6c6e-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="b6c6e-106">U ostatních databází použijte mechanizmus hostování, který poskytuje tato databáze.</span><span class="sxs-lookup"><span data-stu-id="b6c6e-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a><span data-ttu-id="b6c6e-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6c6e-107">Parameters</span></span>

`disposing`\
<span data-ttu-id="b6c6e-108">`true` pro vydání spravovaných i nespravovaných prostředků; `false` pro vydání pouze nespravovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="b6c6e-108">`true` to release both managed and unmanaged resources; `false` to release only unmanaged resources.</span></span>

## <a name="remarks"></a><span data-ttu-id="b6c6e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b6c6e-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="b6c6e-110">Metoda `SqlStreamChars.Dispose` je soukromá a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="b6c6e-110">The `SqlStreamChars.Dispose` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="b6c6e-111">Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b6c6e-111">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="b6c6e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b6c6e-112">Requirements</span></span>

<span data-ttu-id="b6c6e-113">**Obor názvů:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="b6c6e-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="b6c6e-114">**Sestavení:** System. data (v System. data. dll)</span><span class="sxs-lookup"><span data-stu-id="b6c6e-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="b6c6e-115">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="b6c6e-115">**.NET Framework versions:** Available since 2.0.</span></span>
