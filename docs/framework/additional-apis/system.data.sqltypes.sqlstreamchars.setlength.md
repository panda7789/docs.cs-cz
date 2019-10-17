---
title: SqlStreamChars. SetLength (Int64) – metoda (System. data. SqlTypes)
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
ms.openlocfilehash: 291d6e9395581f2370dafc728521a314d54a686d
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395728"
---
# <a name="sqlstreamcharssetlengthint64-method"></a><span data-ttu-id="82c62-102">SqlStreamChars. SetLength (Int64) – metoda</span><span class="sxs-lookup"><span data-stu-id="82c62-102">SqlStreamChars.SetLength(Int64) Method</span></span>

<span data-ttu-id="82c62-103">Při přepsání v odvozené třídě uvolní prostředky používané datovým proudem.</span><span class="sxs-lookup"><span data-stu-id="82c62-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="82c62-104">Sestavení, které obsahuje tuto metodu, má relaci typu Friend s SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="82c62-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="82c62-105">Je určena pro použití v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="82c62-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="82c62-106">U ostatních databází použijte mechanizmus hostování, který poskytuje tato databáze.</span><span class="sxs-lookup"><span data-stu-id="82c62-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void SetLength (long value);
```

## <a name="parameters"></a><span data-ttu-id="82c62-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="82c62-107">Parameters</span></span>

`value`\
<span data-ttu-id="82c62-108">Požadovaná délka aktuálního datového proudu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="82c62-108">The desired length of the current stream in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="82c62-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="82c62-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="82c62-110">Metoda `SqlStreamChars.SetLength` je soukromá a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="82c62-110">The `SqlStreamChars.SetLength` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="82c62-111">Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="82c62-111">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="82c62-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82c62-112">Requirements</span></span>

<span data-ttu-id="82c62-113">**Obor názvů:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="82c62-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="82c62-114">**Sestavení:** System. data (v System. data. dll)</span><span class="sxs-lookup"><span data-stu-id="82c62-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="82c62-115">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="82c62-115">**.NET Framework versions:** Available since 2.0.</span></span>
