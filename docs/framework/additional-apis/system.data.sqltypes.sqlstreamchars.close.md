---
title: SqlStreamChars.Close Method (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Close
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 942ee987f1c56abe2cb1718347886dd397e7217e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634346"
---
# <a name="sqlstreamcharsclose-method"></a><span data-ttu-id="91956-102">SqlStreamChars.Close – metoda</span><span class="sxs-lookup"><span data-stu-id="91956-102">SqlStreamChars.Close Method</span></span>

<span data-ttu-id="91956-103">Aktuální datový proud se zavře a uvolní všechny prostředky systému přidruženého datového proudu.</span><span class="sxs-lookup"><span data-stu-id="91956-103">Closes the current stream and releases any system resources associated with the stream.</span></span> <span data-ttu-id="91956-104">Sestavení, který obsahuje tato metoda má relaci typu friend s SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="91956-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="91956-105">Je určena pro použití systémem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="91956-105">It's intended for use by SQL Server.</span></span><span data-ttu-id="91956-106"> U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.</span><span class="sxs-lookup"><span data-stu-id="91956-106"> For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public virtual void Close ();
```

## <a name="remarks"></a><span data-ttu-id="91956-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="91956-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="91956-108">`SqlStreamChars.Close` Metoda je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="91956-108">The `SqlStreamChars.Close` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="91956-109">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="91956-109">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="91956-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91956-110">Requirements</span></span>

<span data-ttu-id="91956-111">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="91956-111">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="91956-112">**Sestavení:** System.Data (v System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="91956-112">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="91956-113">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="91956-113">**.NET Framework versions:** Available since 2.0.</span></span>
