---
title: Metoda SqlStreamChars.Read (Char [], Int32, Int32) (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Read
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: df92acfd4050eb16d3a101b20b9b44560273f4d5
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/29/2019
ms.locfileid: "58633644"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a><span data-ttu-id="59f9e-102">Metoda SqlStreamChars.Read (Char [], Int32, Int32)</span><span class="sxs-lookup"><span data-stu-id="59f9e-102">SqlStreamChars.Read(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="59f9e-103">Při přepisu v odvozené třídě, načte další sadu znaků ze vstupního datového proudu.</span><span class="sxs-lookup"><span data-stu-id="59f9e-103">When overridden in a derived class, reads the next set of characters from the input stream.</span></span> <span data-ttu-id="59f9e-104">Sestavení, který obsahuje tato metoda má relaci typu friend s SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="59f9e-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="59f9e-105">Je určena pro použití systémem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="59f9e-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="59f9e-106">U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.</span><span class="sxs-lookup"><span data-stu-id="59f9e-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="59f9e-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="59f9e-107">Parameters</span></span>

`buffer`\
<span data-ttu-id="59f9e-108">Pole znaků ke čtení.</span><span class="sxs-lookup"><span data-stu-id="59f9e-108">A char array to read.</span></span>

`offset`\
<span data-ttu-id="59f9e-109">Posun vzhledem k počátku.</span><span class="sxs-lookup"><span data-stu-id="59f9e-109">An offset relative to origin.</span></span>

`count`\
<span data-ttu-id="59f9e-110">Počet znaků ke čtení z aktuální datový proud.</span><span class="sxs-lookup"><span data-stu-id="59f9e-110">The number of characters to be read from the current stream.</span></span>

## <a name="returns"></a><span data-ttu-id="59f9e-111">Vrací</span><span class="sxs-lookup"><span data-stu-id="59f9e-111">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="59f9e-112">Celkový počet znaků do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="59f9e-112">The total number of characters read into the buffer.</span></span>

## <a name="remarks"></a><span data-ttu-id="59f9e-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="59f9e-113">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="59f9e-114">`SqlStreamChars.Read` Metoda je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="59f9e-114">The `SqlStreamChars.Read` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="59f9e-115">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="59f9e-115">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="59f9e-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="59f9e-116">Requirements</span></span>

<span data-ttu-id="59f9e-117">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="59f9e-117">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="59f9e-118">**Sestavení:** System.Data (v System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="59f9e-118">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="59f9e-119">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="59f9e-119">**.NET Framework versions:** Available since 2.0.</span></span>