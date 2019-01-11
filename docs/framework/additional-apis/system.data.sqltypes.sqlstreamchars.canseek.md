---
title: Vlastnost SqlStreamChars.CanSeek (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 8d7bd7fb90177932b413c379f618a6d36374de57
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54223140"
---
# <a name="sqlstreamcharscanseek-property"></a><span data-ttu-id="9a09d-102">Vlastnost SqlStreamChars.CanSeek</span><span class="sxs-lookup"><span data-stu-id="9a09d-102">SqlStreamChars.CanSeek Property</span></span>

<span data-ttu-id="9a09d-103">Při přepisu v odvozené třídě získá hodnotu, která určuje, zda aktuální datový proud podporuje operace seek.</span><span class="sxs-lookup"><span data-stu-id="9a09d-103">When overridden in a derived class, gets a value that indicates whether the current steam supports the seek operation.</span></span> <span data-ttu-id="9a09d-104">Sestavení, který obsahuje tato vlastnost má relaci typu friend s SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="9a09d-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="9a09d-105">Je určena pro použití systémem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9a09d-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="9a09d-106">U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.</span><span class="sxs-lookup"><span data-stu-id="9a09d-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a><span data-ttu-id="9a09d-107">Hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9a09d-107">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="9a09d-108">`true` Pokud aktuální datový proud podporuje operace seek; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="9a09d-108">`true` if the current steam supports the seek operation; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="9a09d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9a09d-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="9a09d-110">`SqlStreamChars.CanSeek` Vlastnost je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="9a09d-110">The `SqlStreamChars.CanSeek` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="9a09d-111">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="9a09d-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="9a09d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9a09d-112">Requirements</span></span>

<span data-ttu-id="9a09d-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="9a09d-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="9a09d-114">**Sestavení:** System.Data (v System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="9a09d-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="9a09d-115">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="9a09d-115">**.NET Framework versions:** Available since 2.0.</span></span>