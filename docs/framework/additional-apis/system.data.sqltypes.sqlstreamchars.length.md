---
title: Vlastnost SqlStreamChars.Length (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: ac6e6af9c9411ebc25039e0992133fae2b35ee23
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221178"
---
# <a name="sqlstreamcharslength-property"></a><span data-ttu-id="e662d-102">Vlastnost SqlStreamChars.Length</span><span class="sxs-lookup"><span data-stu-id="e662d-102">SqlStreamChars.Length Property</span></span>

<span data-ttu-id="e662d-103">Při přepisu v odvozené třídě, získá délku aktuální datový proud.</span><span class="sxs-lookup"><span data-stu-id="e662d-103">When overridden in a derived class, gets the length of the current stream.</span></span> <span data-ttu-id="e662d-104">Sestavení, který obsahuje tato vlastnost má relaci typu friend s SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="e662d-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="e662d-105">Je určena pro použití systémem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e662d-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="e662d-106">U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.</span><span class="sxs-lookup"><span data-stu-id="e662d-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="e662d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e662d-107">Syntax</span></span>

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a><span data-ttu-id="e662d-108">Hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e662d-108">Property value</span></span>

<xref:System.Int64>\
<span data-ttu-id="e662d-109">Délku datového proudu.</span><span class="sxs-lookup"><span data-stu-id="e662d-109">The length of the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="e662d-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e662d-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="e662d-111">`SqlStreamChars.Length` Vlastnost je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="e662d-111">The `SqlStreamChars.Length` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="e662d-112">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="e662d-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e662d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e662d-113">Requirements</span></span>

<span data-ttu-id="e662d-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="e662d-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="e662d-115">**Sestavení:** System.Data (v System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="e662d-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="e662d-116">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="e662d-116">**.NET Framework versions:** Available since 2.0.</span></span>