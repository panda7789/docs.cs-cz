---
title: SqlStreamChars. Close – metoda (System. data. SqlTypes)
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
ms.openlocfilehash: c33c60842d181be7011528ca7550f3d09f291f43
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395638"
---
# <a name="sqlstreamcharsclose-method"></a><span data-ttu-id="e00f1-102">SqlStreamChars. Close – metoda</span><span class="sxs-lookup"><span data-stu-id="e00f1-102">SqlStreamChars.Close Method</span></span>

<span data-ttu-id="e00f1-103">Zavře aktuální datový proud a uvolní všechny systémové prostředky přidružené ke streamu.</span><span class="sxs-lookup"><span data-stu-id="e00f1-103">Closes the current stream and releases any system resources associated with the stream.</span></span> <span data-ttu-id="e00f1-104">Sestavení, které obsahuje tuto metodu, má relaci typu Friend s SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="e00f1-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="e00f1-105">Je určena pro použití v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e00f1-105">It's intended for use by SQL Server.</span></span><span data-ttu-id="e00f1-106"> U ostatních databází použijte mechanizmus hostování, který poskytuje tato databáze.</span><span class="sxs-lookup"><span data-stu-id="e00f1-106"> For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public virtual void Close ();
```

## <a name="remarks"></a><span data-ttu-id="e00f1-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e00f1-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="e00f1-108">Metoda `SqlStreamChars.Close` je soukromá a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="e00f1-108">The `SqlStreamChars.Close` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="e00f1-109">Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e00f1-109">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e00f1-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e00f1-110">Requirements</span></span>

<span data-ttu-id="e00f1-111">**Obor názvů:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="e00f1-111">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="e00f1-112">**Sestavení:** System. data (v System. data. dll)</span><span class="sxs-lookup"><span data-stu-id="e00f1-112">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="e00f1-113">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="e00f1-113">**.NET Framework versions:** Available since 2.0.</span></span>
