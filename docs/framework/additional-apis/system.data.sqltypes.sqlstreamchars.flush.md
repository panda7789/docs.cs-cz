---
title: Metoda SqlStreamChars.Flush (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.Flush
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: ecaf7932a4e832a88b883ceac4746afe6140b38e
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152242"
---
# <a name="sqlstreamcharsflush-method"></a><span data-ttu-id="95d42-102">SqlStreamChars.Flush – metoda</span><span class="sxs-lookup"><span data-stu-id="95d42-102">SqlStreamChars.Flush Method</span></span>

<span data-ttu-id="95d42-103">Při přepisu v odvozené třídě, vymaže všechny vyrovnávací paměti pro tento datový proud a způsobí, že všechna data ve vyrovnávací paměti k zápisu do základní zařízení.</span><span class="sxs-lookup"><span data-stu-id="95d42-103">When overridden in a derived class, clears all buffers for this stream and causes any buffered data to be written to the underlying device.</span></span> <span data-ttu-id="95d42-104">Sestavení, který obsahuje tato metoda má relaci typu friend s SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="95d42-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="95d42-105">Je určena pro použití systémem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="95d42-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="95d42-106">U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.</span><span class="sxs-lookup"><span data-stu-id="95d42-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="95d42-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95d42-107">Syntax</span></span>

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a><span data-ttu-id="95d42-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="95d42-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="95d42-109">`SqlStreamChars.Flush` Metoda je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="95d42-109">The `SqlStreamChars.Flush` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="95d42-110">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="95d42-110">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="95d42-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="95d42-111">Requirements</span></span>

<span data-ttu-id="95d42-112">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="95d42-112">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="95d42-113">**Sestavení:** System.Data (v System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="95d42-113">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="95d42-114">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="95d42-114">**.NET Framework versions:** Available since 2.0.</span></span>