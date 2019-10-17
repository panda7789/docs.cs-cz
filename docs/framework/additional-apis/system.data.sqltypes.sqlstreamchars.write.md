---
title: SqlStreamChars. Write – metoda (Char [], Int32, Int32) (System. data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 9d952041122ceb3824712bd81cab7ce4789c9db8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395575"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a><span data-ttu-id="85715-102">SqlStreamChars. Write – metoda (Char [], Int32, Int32)</span><span class="sxs-lookup"><span data-stu-id="85715-102">SqlStreamChars.Write(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="85715-103">Při přepsání v odvozené třídě zapíše posloupnost znaků do aktuálního datového proudu a Posune aktuální pozici v rámci tohoto datového proudu o počet zapsaných znaků.</span><span class="sxs-lookup"><span data-stu-id="85715-103">When overridden in a derived class, writes a sequence of characters to the current stream and advances the current position within this stream by the number of characters written.</span></span> <span data-ttu-id="85715-104">Sestavení, které obsahuje tuto metodu, má relaci typu Friend s SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="85715-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="85715-105">Je určena pro použití v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="85715-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="85715-106">U ostatních databází použijte mechanizmus hostování, který poskytuje tato databáze.</span><span class="sxs-lookup"><span data-stu-id="85715-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="85715-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="85715-107">Parameters</span></span>

`buffer`  
<span data-ttu-id="85715-108">Pole znaků, které se má zapsat</span><span class="sxs-lookup"><span data-stu-id="85715-108">A char array to write.</span></span>

`offset`  
<span data-ttu-id="85715-109">Posun vzhledem ke zdroji.</span><span class="sxs-lookup"><span data-stu-id="85715-109">An offset relative to origin.</span></span>

`count`  
<span data-ttu-id="85715-110">Počet znaků, které mají být zapsány do aktuálního datového proudu.</span><span class="sxs-lookup"><span data-stu-id="85715-110">The number of characters to be written to the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="85715-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="85715-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="85715-112">Metoda `SqlStreamChars.Write` je soukromá a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="85715-112">The `SqlStreamChars.Write` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="85715-113">Společnost Microsoft nepodporuje použití této metody zápisu do produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="85715-113">Microsoft does not support the use of this method write in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="85715-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="85715-114">Requirements</span></span>

<span data-ttu-id="85715-115">**Obor názvů:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="85715-115">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="85715-116">**Sestavení:** System. data (v System. data. dll)</span><span class="sxs-lookup"><span data-stu-id="85715-116">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="85715-117">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="85715-117">**.NET Framework versions:** Available since 2.0.</span></span>
