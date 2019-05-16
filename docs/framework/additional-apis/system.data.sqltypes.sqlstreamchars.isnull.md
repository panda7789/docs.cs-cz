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
ms.openlocfilehash: 03b702b0ffe258eb8cad0a1ece5314b363f9a0d0
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634617"
---
# <a name="sqlstreamcharsisnull-property"></a><span data-ttu-id="d3494-102">SqlStreamChars.IsNull Property</span><span class="sxs-lookup"><span data-stu-id="d3494-102">SqlStreamChars.IsNull Property</span></span>

<span data-ttu-id="d3494-103">Při přepisu v odvozené třídě získá hodnotu, která určuje, zda je datový proud `null`.</span><span class="sxs-lookup"><span data-stu-id="d3494-103">When overridden in a derived class, gets a value that indicates whether the stream is `null`.</span></span> <span data-ttu-id="d3494-104">Sestavení, který obsahuje tato vlastnost má relaci typu friend s SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="d3494-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="d3494-105">Je určena pro použití systémem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d3494-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="d3494-106">U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.</span><span class="sxs-lookup"><span data-stu-id="d3494-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="d3494-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3494-107">Syntax</span></span>

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a><span data-ttu-id="d3494-108">Hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d3494-108">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="d3494-109">`true` Pokud je datový proud `null`; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="d3494-109">`true` if the stream is `null`; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="d3494-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d3494-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="d3494-111">`SqlStreamChars.IsNull` Vlastnost je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="d3494-111">The `SqlStreamChars.IsNull` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="d3494-112">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="d3494-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="d3494-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d3494-113">Requirements</span></span>

<span data-ttu-id="d3494-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="d3494-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="d3494-115">**Sestavení:** System.Data (v System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="d3494-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="d3494-116">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="d3494-116">**.NET Framework versions:** Available since 2.0.</span></span>
