---
title: SqlStreamChars. CanSeek – vlastnost (System. data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: eb32978f62b7d46f0abf715e2bca347592c0fda8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395782"
---
# <a name="sqlstreamcharscanseek-property"></a><span data-ttu-id="e419c-102">SqlStreamChars. CanSeek – vlastnost</span><span class="sxs-lookup"><span data-stu-id="e419c-102">SqlStreamChars.CanSeek Property</span></span>

<span data-ttu-id="e419c-103">Při přepsání v odvozené třídě získá hodnotu, která označuje, zda aktuální pára podporuje operaci hledání.</span><span class="sxs-lookup"><span data-stu-id="e419c-103">When overridden in a derived class, gets a value that indicates whether the current steam supports the seek operation.</span></span> <span data-ttu-id="e419c-104">Sestavení, které obsahuje tuto vlastnost, má relaci typu Friend s SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="e419c-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="e419c-105">Je určena pro použití v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e419c-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="e419c-106">U ostatních databází použijte mechanizmus hostování, který poskytuje tato databáze.</span><span class="sxs-lookup"><span data-stu-id="e419c-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a><span data-ttu-id="e419c-107">Hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e419c-107">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="e419c-108">`true`, pokud aktuální pára podporuje operaci hledání; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="e419c-108">`true` if the current steam supports the seek operation; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="e419c-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e419c-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="e419c-110">Vlastnost `SqlStreamChars.CanSeek` je soukromá a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="e419c-110">The `SqlStreamChars.CanSeek` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="e419c-111">Společnost Microsoft v žádné situaci nepodporuje použití této vlastnosti v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e419c-111">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e419c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e419c-112">Requirements</span></span>

<span data-ttu-id="e419c-113">**Obor názvů:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="e419c-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="e419c-114">**Sestavení:** System. data (v System. data. dll)</span><span class="sxs-lookup"><span data-stu-id="e419c-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="e419c-115">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="e419c-115">**.NET Framework versions:** Available since 2.0.</span></span>
