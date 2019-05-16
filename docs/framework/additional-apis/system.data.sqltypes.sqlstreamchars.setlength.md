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
ms.openlocfilehash: 6bdf7bf5b998135652bc63d8d3e6c71a61475d20
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634297"
---
# <a name="sqlstreamcharssetlengthint64-method"></a><span data-ttu-id="ef969-102">SqlStreamChars.SetLength(Int64) – metoda</span><span class="sxs-lookup"><span data-stu-id="ef969-102">SqlStreamChars.SetLength(Int64) Method</span></span>

<span data-ttu-id="ef969-103">Při přepisu v odvozené třídě, uvolní prostředky využívané třídou datového proudu.</span><span class="sxs-lookup"><span data-stu-id="ef969-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="ef969-104">Sestavení, který obsahuje tato metoda má relaci typu friend s SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="ef969-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="ef969-105">Je určena pro použití systémem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ef969-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="ef969-106">U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.</span><span class="sxs-lookup"><span data-stu-id="ef969-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void SetLength (long value);
```

## <a name="parameters"></a><span data-ttu-id="ef969-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef969-107">Parameters</span></span>

`value`\
<span data-ttu-id="ef969-108">Požadovaná délka aktuální datový proud v bajtech.</span><span class="sxs-lookup"><span data-stu-id="ef969-108">The desired length of the current stream in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="ef969-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ef969-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="ef969-110">`SqlStreamChars.SetLength` Metoda je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="ef969-110">The `SqlStreamChars.SetLength` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="ef969-111">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="ef969-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="ef969-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ef969-112">Requirements</span></span>

<span data-ttu-id="ef969-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="ef969-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="ef969-114">**Sestavení:** System.Data (v System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="ef969-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="ef969-115">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="ef969-115">**.NET Framework versions:** Available since 2.0.</span></span>
