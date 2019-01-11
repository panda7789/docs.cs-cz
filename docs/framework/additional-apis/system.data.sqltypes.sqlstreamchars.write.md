---
title: Metoda SqlStreamChars.Write (Char [], Int32, Int32) (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: dd9bb691f6d07f4875d684eef76d6329667003af
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221905"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a><span data-ttu-id="37971-102">Metoda SqlStreamChars.Write (Char [], Int32, Int32)</span><span class="sxs-lookup"><span data-stu-id="37971-102">SqlStreamChars.Write(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="37971-103">Při přepisu v odvozené třídě, zapíše posloupnost znaků do aktuální datový proud a posune aktuální pozici v rámci tohoto datového proudu o počet napsaných znaků.</span><span class="sxs-lookup"><span data-stu-id="37971-103">When overridden in a derived class, writes a sequence of characters to the current stream and advances the current position within this stream by the number of characters written.</span></span> <span data-ttu-id="37971-104">Sestavení, který obsahuje tato metoda má relaci typu friend s SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="37971-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="37971-105">Je určena pro použití systémem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="37971-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="37971-106">U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.</span><span class="sxs-lookup"><span data-stu-id="37971-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="37971-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="37971-107">Parameters</span></span>

`buffer`  
<span data-ttu-id="37971-108">Pole znaků k zápisu.</span><span class="sxs-lookup"><span data-stu-id="37971-108">A char array to write.</span></span>

`offset`  
<span data-ttu-id="37971-109">Posun vzhledem k počátku.</span><span class="sxs-lookup"><span data-stu-id="37971-109">An offset relative to origin.</span></span>

`count`  
<span data-ttu-id="37971-110">Počet znaků k zápisu do aktuální datový proud.</span><span class="sxs-lookup"><span data-stu-id="37971-110">The number of characters to be written to the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="37971-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37971-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="37971-112">`SqlStreamChars.Write` Metoda je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="37971-112">The `SqlStreamChars.Write` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="37971-113">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="37971-113">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="37971-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37971-114">Requirements</span></span>

<span data-ttu-id="37971-115">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="37971-115">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="37971-116">**Sestavení:** System.Data (v System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="37971-116">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="37971-117">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="37971-117">**.NET Framework versions:** Available since 2.0.</span></span>