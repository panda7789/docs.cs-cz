---
title: Metoda SqlStreamChars.SetLength(Int64) (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.SetLength
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: c7199cbd08e62b1f0391437a0c1864cb9036fe1f
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222692"
---
# <a name="sqlstreamcharssetlengthint64-method"></a><span data-ttu-id="e887d-102">SqlStreamChars.SetLength(Int64) – metoda</span><span class="sxs-lookup"><span data-stu-id="e887d-102">SqlStreamChars.SetLength(Int64) Method</span></span>

<span data-ttu-id="e887d-103">Při přepisu v odvozené třídě, uvolní prostředky využívané třídou datového proudu.</span><span class="sxs-lookup"><span data-stu-id="e887d-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="e887d-104">Sestavení, který obsahuje tato metoda má relaci typu friend s SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="e887d-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="e887d-105">Je určena pro použití systémem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e887d-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="e887d-106">U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.</span><span class="sxs-lookup"><span data-stu-id="e887d-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void SetLength (long value);
```

## <a name="parameters"></a><span data-ttu-id="e887d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="e887d-107">Parameters</span></span>

`value`\
<span data-ttu-id="e887d-108">Požadovaná délka aktuální datový proud v bajtech.</span><span class="sxs-lookup"><span data-stu-id="e887d-108">The desired length of the current stream in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="e887d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e887d-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="e887d-110">`SqlStreamChars.SetLength` Metoda je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="e887d-110">The `SqlStreamChars.SetLength` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="e887d-111">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="e887d-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e887d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e887d-112">Requirements</span></span>

<span data-ttu-id="e887d-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="e887d-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="e887d-114">**Sestavení:** System.Data (v System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="e887d-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="e887d-115">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="e887d-115">**.NET Framework versions:** Available since 2.0.</span></span>