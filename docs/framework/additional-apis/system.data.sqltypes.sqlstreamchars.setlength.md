---
title: Metoda SqlStreamChars.SetLength(Int64) (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.SetLength
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 1283fea83cf77bbc898d460feedc72b898a65fb7
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/29/2019
ms.locfileid: "58633943"
---
# <a name="sqlstreamcharssetlengthint64-method"></a><span data-ttu-id="0ca63-102">SqlStreamChars.SetLength(Int64) – metoda</span><span class="sxs-lookup"><span data-stu-id="0ca63-102">SqlStreamChars.SetLength(Int64) Method</span></span>

<span data-ttu-id="0ca63-103">Při přepisu v odvozené třídě, uvolní prostředky využívané třídou datového proudu.</span><span class="sxs-lookup"><span data-stu-id="0ca63-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="0ca63-104">Sestavení, který obsahuje tato metoda má relaci typu friend s SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="0ca63-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="0ca63-105">Je určena pro použití systémem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0ca63-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="0ca63-106">U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.</span><span class="sxs-lookup"><span data-stu-id="0ca63-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void SetLength (long value);
```

## <a name="parameters"></a><span data-ttu-id="0ca63-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ca63-107">Parameters</span></span>

`value`\
<span data-ttu-id="0ca63-108">Požadovaná délka aktuální datový proud v bajtech.</span><span class="sxs-lookup"><span data-stu-id="0ca63-108">The desired length of the current stream in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="0ca63-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ca63-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="0ca63-110">`SqlStreamChars.SetLength` Metoda je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="0ca63-110">The `SqlStreamChars.SetLength` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="0ca63-111">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="0ca63-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="0ca63-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ca63-112">Requirements</span></span>

<span data-ttu-id="0ca63-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="0ca63-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="0ca63-114">**Sestavení:** System.Data (v System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="0ca63-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="0ca63-115">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="0ca63-115">**.NET Framework versions:** Available since 2.0.</span></span>