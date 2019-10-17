---
title: SqlStreamChars. IsNull – vlastnost (System. data. SqlTypes)
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
ms.openlocfilehash: d80f653724b3ef0a1cadb69a5f72b1d9455597d6
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395738"
---
# <a name="sqlstreamcharsisnull-property"></a><span data-ttu-id="263ae-102">SqlStreamChars. IsNull – vlastnost</span><span class="sxs-lookup"><span data-stu-id="263ae-102">SqlStreamChars.IsNull Property</span></span>

<span data-ttu-id="263ae-103">Při přepsání v odvozené třídě získá hodnotu, která označuje, zda je datový proud `null`.</span><span class="sxs-lookup"><span data-stu-id="263ae-103">When overridden in a derived class, gets a value that indicates whether the stream is `null`.</span></span> <span data-ttu-id="263ae-104">Sestavení, které obsahuje tuto vlastnost, má relaci typu Friend s SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="263ae-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="263ae-105">Je určena pro použití v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="263ae-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="263ae-106">U ostatních databází použijte mechanizmus hostování, který poskytuje tato databáze.</span><span class="sxs-lookup"><span data-stu-id="263ae-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="263ae-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="263ae-107">Syntax</span></span>

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a><span data-ttu-id="263ae-108">Hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="263ae-108">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="263ae-109">`true`, pokud je datový proud `null`; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="263ae-109">`true` if the stream is `null`; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="263ae-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="263ae-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="263ae-111">Vlastnost `SqlStreamChars.IsNull` je soukromá a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="263ae-111">The `SqlStreamChars.IsNull` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="263ae-112">Společnost Microsoft v žádné situaci nepodporuje použití této vlastnosti v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="263ae-112">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="263ae-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="263ae-113">Requirements</span></span>

<span data-ttu-id="263ae-114">**Obor názvů:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="263ae-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="263ae-115">**Sestavení:** System. data (v System. data. dll)</span><span class="sxs-lookup"><span data-stu-id="263ae-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="263ae-116">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="263ae-116">**.NET Framework versions:** Available since 2.0.</span></span>
