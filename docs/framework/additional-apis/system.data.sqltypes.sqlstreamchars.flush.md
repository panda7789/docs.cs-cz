---
title: SqlStreamChars. Flush – metoda (System. data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Flush
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 38ade5ce38cfe5003b2d06c0d8bb2db1a20bc05b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395616"
---
# <a name="sqlstreamcharsflush-method"></a><span data-ttu-id="52ecf-102">SqlStreamChars. Flush – metoda</span><span class="sxs-lookup"><span data-stu-id="52ecf-102">SqlStreamChars.Flush Method</span></span>

<span data-ttu-id="52ecf-103">Při přepsání v odvozené třídě vymaže všechny vyrovnávací paměti pro tento datový proud a způsobí, že všechna data uložená do vyrovnávací paměti budou zapsána do základního zařízení.</span><span class="sxs-lookup"><span data-stu-id="52ecf-103">When overridden in a derived class, clears all buffers for this stream and causes any buffered data to be written to the underlying device.</span></span> <span data-ttu-id="52ecf-104">Sestavení, které obsahuje tuto metodu, má relaci typu Friend s SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="52ecf-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="52ecf-105">Je určena pro použití v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="52ecf-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="52ecf-106">U ostatních databází použijte mechanizmus hostování, který poskytuje tato databáze.</span><span class="sxs-lookup"><span data-stu-id="52ecf-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="52ecf-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52ecf-107">Syntax</span></span>

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a><span data-ttu-id="52ecf-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52ecf-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="52ecf-109">Metoda `SqlStreamChars.Flush` je soukromá a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="52ecf-109">The `SqlStreamChars.Flush` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="52ecf-110">Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="52ecf-110">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="52ecf-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52ecf-111">Requirements</span></span>

<span data-ttu-id="52ecf-112">**Obor názvů:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="52ecf-112">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="52ecf-113">**Sestavení:** System. data (v System. data. dll)</span><span class="sxs-lookup"><span data-stu-id="52ecf-113">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="52ecf-114">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="52ecf-114">**.NET Framework versions:** Available since 2.0.</span></span>
