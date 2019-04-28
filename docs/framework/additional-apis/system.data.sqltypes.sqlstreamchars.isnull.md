---
title: SqlStreamChars.IsNull Property (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: ec00b0afa1597c3ae6488c12fe5a0667dad70e2d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675218"
---
# <a name="sqlstreamcharsisnull-property"></a><span data-ttu-id="897d9-102">SqlStreamChars.IsNull Property</span><span class="sxs-lookup"><span data-stu-id="897d9-102">SqlStreamChars.IsNull Property</span></span>

<span data-ttu-id="897d9-103">Při přepisu v odvozené třídě získá hodnotu, která určuje, zda je datový proud `null`.</span><span class="sxs-lookup"><span data-stu-id="897d9-103">When overridden in a derived class, gets a value that indicates whether the stream is `null`.</span></span> <span data-ttu-id="897d9-104">Sestavení, který obsahuje tato vlastnost má relaci typu friend s SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="897d9-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="897d9-105">Je určena pro použití systémem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="897d9-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="897d9-106">U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.</span><span class="sxs-lookup"><span data-stu-id="897d9-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="897d9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="897d9-107">Syntax</span></span>

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a><span data-ttu-id="897d9-108">Hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="897d9-108">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="897d9-109">`true` Pokud je datový proud `null`; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="897d9-109">`true` if the stream is `null`; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="897d9-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="897d9-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="897d9-111">`SqlStreamChars.IsNull` Vlastnost je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="897d9-111">The `SqlStreamChars.IsNull` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="897d9-112">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="897d9-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="897d9-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="897d9-113">Requirements</span></span>

<span data-ttu-id="897d9-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="897d9-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="897d9-115">**Sestavení:** System.Data (v System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="897d9-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="897d9-116">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="897d9-116">**.NET Framework versions:** Available since 2.0.</span></span>