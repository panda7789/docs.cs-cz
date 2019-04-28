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
ms.openlocfilehash: d0c29bbc5c6bea98cf36e3c2b6bf7825d6843ccc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705867"
---
# <a name="sqlstreamcharsclose-method"></a><span data-ttu-id="a5069-102">SqlStreamChars.Close – metoda</span><span class="sxs-lookup"><span data-stu-id="a5069-102">SqlStreamChars.Close Method</span></span>

<span data-ttu-id="a5069-103">Aktuální datový proud se zavře a uvolní všechny prostředky systému přidruženého datového proudu.</span><span class="sxs-lookup"><span data-stu-id="a5069-103">Closes the current stream and releases any system resources associated with the stream.</span></span> <span data-ttu-id="a5069-104">Sestavení, který obsahuje tato metoda má relaci typu friend s SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="a5069-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="a5069-105">Je určena pro použití systémem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a5069-105">It's intended for use by SQL Server.</span></span><span data-ttu-id="a5069-106"> U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.</span><span class="sxs-lookup"><span data-stu-id="a5069-106"> For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public virtual void Close ();
```

## <a name="remarks"></a><span data-ttu-id="a5069-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5069-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="a5069-108">`SqlStreamChars.Close` Metoda je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="a5069-108">The `SqlStreamChars.Close` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="a5069-109">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="a5069-109">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="a5069-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a5069-110">Requirements</span></span>

<span data-ttu-id="a5069-111">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="a5069-111">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="a5069-112">**Sestavení:** System.Data (v System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="a5069-112">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="a5069-113">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="a5069-113">**.NET Framework versions:** Available since 2.0.</span></span>