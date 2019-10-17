---
title: SqlStreamChars. Length – vlastnost (System. data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 2171b10d1c0eb7bcad894cc44c5103bdab18b0a5
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395610"
---
# <a name="sqlstreamcharslength-property"></a><span data-ttu-id="3d777-102">SqlStreamChars. Length – vlastnost</span><span class="sxs-lookup"><span data-stu-id="3d777-102">SqlStreamChars.Length Property</span></span>

<span data-ttu-id="3d777-103">Při přepsání v odvozené třídě získá délku aktuálního datového proudu.</span><span class="sxs-lookup"><span data-stu-id="3d777-103">When overridden in a derived class, gets the length of the current stream.</span></span> <span data-ttu-id="3d777-104">Sestavení, které obsahuje tuto vlastnost, má relaci typu Friend s SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="3d777-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="3d777-105">Je určena pro použití v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3d777-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="3d777-106">U ostatních databází použijte mechanizmus hostování, který poskytuje tato databáze.</span><span class="sxs-lookup"><span data-stu-id="3d777-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="3d777-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d777-107">Syntax</span></span>

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a><span data-ttu-id="3d777-108">Hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3d777-108">Property value</span></span>

<xref:System.Int64>\
<span data-ttu-id="3d777-109">Délka datového proudu.</span><span class="sxs-lookup"><span data-stu-id="3d777-109">The length of the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="3d777-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d777-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="3d777-111">Vlastnost `SqlStreamChars.Length` je soukromá a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="3d777-111">The `SqlStreamChars.Length` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="3d777-112">Společnost Microsoft v žádné situaci nepodporuje použití této vlastnosti v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3d777-112">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="3d777-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3d777-113">Requirements</span></span>

<span data-ttu-id="3d777-114">**Obor názvů:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="3d777-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="3d777-115">**Sestavení:** System. data (v System. data. dll)</span><span class="sxs-lookup"><span data-stu-id="3d777-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="3d777-116">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="3d777-116">**.NET Framework versions:** Available since 2.0.</span></span>
