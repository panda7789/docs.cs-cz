---
title: SqlChars.Stream Property (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology:
- dotnet-data
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
ms.openlocfilehash: 36a6b3f45f0832ed651dc0a613f50e7170517497
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827679"
---
# <a name="sqlcharsstream-property"></a><span data-ttu-id="e2c85-102">SqlChars.Stream Property</span><span class="sxs-lookup"><span data-stu-id="e2c85-102">SqlChars.Stream Property</span></span>

<span data-ttu-id="e2c85-103">Získá nebo nastaví datového proudu znaků.</span><span class="sxs-lookup"><span data-stu-id="e2c85-103">Gets or sets the character stream.</span></span> <span data-ttu-id="e2c85-104">Sestavení, který obsahuje tato vlastnost má relaci typu friend s SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="e2c85-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="e2c85-105">Je určena pro použití systémem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e2c85-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="e2c85-106">U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.</span><span class="sxs-lookup"><span data-stu-id="e2c85-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
internal SqlStreamChars Stream { get; set; }
```

## <a name="property-value"></a><span data-ttu-id="e2c85-107">Hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e2c85-107">Property value</span></span>

`System.Data.SqlTypes.SqlStreamChars`\
<span data-ttu-id="e2c85-108">Datového proudu znaků.</span><span class="sxs-lookup"><span data-stu-id="e2c85-108">The character stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="e2c85-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2c85-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="e2c85-110">`SqlChars.Stream` Vlastnost je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="e2c85-110">The `SqlChars.Stream` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="e2c85-111">Microsoft nepodporuje použití této vlastnosti v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="e2c85-111">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e2c85-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2c85-112">Requirements</span></span>

<span data-ttu-id="e2c85-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="e2c85-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="e2c85-114">**Sestavení:** System.Data (v System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="e2c85-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="e2c85-115">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="e2c85-115">**.NET Framework versions:** Available since 2.0.</span></span>