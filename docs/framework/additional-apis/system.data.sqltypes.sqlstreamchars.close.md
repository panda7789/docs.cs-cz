---
title: Metoda SqlStreamChars.Close (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.Close
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 893ee729b864d381c4e4686024687f309d15d214
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152215"
---
# <a name="sqlstreamcharsclose-method"></a><span data-ttu-id="2133c-102">SqlStreamChars.Close – metoda</span><span class="sxs-lookup"><span data-stu-id="2133c-102">SqlStreamChars.Close Method</span></span>

<span data-ttu-id="2133c-103">Aktuální datový proud se zavře a uvolní všechny prostředky systému přidruženého datového proudu.</span><span class="sxs-lookup"><span data-stu-id="2133c-103">Closes the current stream and releases any system resources associated with the stream.</span></span> <span data-ttu-id="2133c-104">Sestavení, který obsahuje tato metoda má relaci typu friend s SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="2133c-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="2133c-105">Je určena pro použití systémem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2133c-105">It's intended for use by SQL Server.</span></span><span data-ttu-id="2133c-106"> U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.</span><span class="sxs-lookup"><span data-stu-id="2133c-106"> For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public virtual void Close ();
```

## <a name="remarks"></a><span data-ttu-id="2133c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2133c-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="2133c-108">`SqlStreamChars.Close` Metoda je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="2133c-108">The `SqlStreamChars.Close` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="2133c-109">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="2133c-109">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="2133c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2133c-110">Requirements</span></span>

<span data-ttu-id="2133c-111">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="2133c-111">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="2133c-112">**Sestavení:** System.Data (v System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="2133c-112">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="2133c-113">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="2133c-113">**.NET Framework versions:** Available since 2.0.</span></span>