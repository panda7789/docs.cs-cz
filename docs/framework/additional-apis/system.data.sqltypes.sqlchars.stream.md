---
title: SqlChars.Stream Property (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlChars.Stream
- System.Data.SqlTypes.SqlChars.get_Stream
- System.Data.SqlTypes.SqlChars.set_Stream
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 4858d9f8878e5b56a0811edf92a2faa729775156
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/29/2019
ms.locfileid: "58633995"
---
# <a name="sqlcharsstream-property"></a><span data-ttu-id="fa3a0-102">SqlChars.Stream – vlastnost</span><span class="sxs-lookup"><span data-stu-id="fa3a0-102">SqlChars.Stream Property</span></span>

<span data-ttu-id="fa3a0-103">Získá nebo nastaví datového proudu znaků.</span><span class="sxs-lookup"><span data-stu-id="fa3a0-103">Gets or sets the character stream.</span></span> <span data-ttu-id="fa3a0-104">Sestavení, který obsahuje tato vlastnost má relaci typu friend s SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="fa3a0-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="fa3a0-105">Je určena pro použití systémem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fa3a0-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="fa3a0-106">U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.</span><span class="sxs-lookup"><span data-stu-id="fa3a0-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
internal SqlStreamChars Stream { get; set; }
```

## <a name="property-value"></a><span data-ttu-id="fa3a0-107">Hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="fa3a0-107">Property value</span></span>

`System.Data.SqlTypes.SqlStreamChars`\
<span data-ttu-id="fa3a0-108">Datového proudu znaků.</span><span class="sxs-lookup"><span data-stu-id="fa3a0-108">The character stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="fa3a0-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fa3a0-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="fa3a0-110">`SqlChars.Stream` Vlastnost je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="fa3a0-110">The `SqlChars.Stream` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="fa3a0-111">Microsoft nepodporuje použití této vlastnosti v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="fa3a0-111">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="fa3a0-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fa3a0-112">Requirements</span></span>

<span data-ttu-id="fa3a0-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="fa3a0-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="fa3a0-114">**Sestavení:** System.Data (v System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="fa3a0-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="fa3a0-115">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="fa3a0-115">**.NET Framework versions:** Available since 2.0.</span></span>