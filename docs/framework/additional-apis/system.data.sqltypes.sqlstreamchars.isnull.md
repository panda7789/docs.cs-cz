---
title: Vlastnost SqlStreamChars.IsNull (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 79ebb9ec54185a94cb95dfd0fb2929e61cf513ef
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152206"
---
# <a name="sqlstreamcharsisnull-property"></a><span data-ttu-id="000f3-102">Vlastnost SqlStreamChars.IsNull</span><span class="sxs-lookup"><span data-stu-id="000f3-102">SqlStreamChars.IsNull Property</span></span>

<span data-ttu-id="000f3-103">Při přepisu v odvozené třídě získá hodnotu, která určuje, zda je datový proud `null`.</span><span class="sxs-lookup"><span data-stu-id="000f3-103">When overridden in a derived class, gets a value that indicates whether the stream is `null`.</span></span> <span data-ttu-id="000f3-104">Sestavení, který obsahuje tato vlastnost má relaci typu friend s SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="000f3-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="000f3-105">Je určena pro použití systémem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="000f3-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="000f3-106">U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.</span><span class="sxs-lookup"><span data-stu-id="000f3-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="000f3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="000f3-107">Syntax</span></span>

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a><span data-ttu-id="000f3-108">Hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="000f3-108">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="000f3-109">`true` Pokud je datový proud `null`; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="000f3-109">`true` if the stream is `null`; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="000f3-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="000f3-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="000f3-111">`SqlStreamChars.IsNull` Vlastnost je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="000f3-111">The `SqlStreamChars.IsNull` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="000f3-112">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="000f3-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="000f3-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="000f3-113">Requirements</span></span>

<span data-ttu-id="000f3-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="000f3-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="000f3-115">**Sestavení:** System.Data (v System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="000f3-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="000f3-116">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="000f3-116">**.NET Framework versions:** Available since 2.0.</span></span>