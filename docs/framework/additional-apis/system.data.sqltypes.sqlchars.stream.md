---
title: Vlastnost SqlChars.Stream (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlChars.Stream
- System.Data.SqlTypes.SqlChars.get_Stream
- System.Data.SqlTypes.SqlChars.set_Stream
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: f8b6f4f3a92f1d78e434263c6a7897641867c412
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152200"
---
# <a name="sqlcharsstream-property"></a><span data-ttu-id="636c4-102">Vlastnost SqlChars.Stream</span><span class="sxs-lookup"><span data-stu-id="636c4-102">SqlChars.Stream Property</span></span>

<span data-ttu-id="636c4-103">Získá nebo nastaví datového proudu znaků.</span><span class="sxs-lookup"><span data-stu-id="636c4-103">Gets or sets the character stream.</span></span> <span data-ttu-id="636c4-104">Sestavení, který obsahuje tato vlastnost má relaci typu friend s SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="636c4-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="636c4-105">Je určena pro použití systémem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="636c4-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="636c4-106">U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.</span><span class="sxs-lookup"><span data-stu-id="636c4-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
internal SqlStreamChars Stream { get; set; }
```

## <a name="property-value"></a><span data-ttu-id="636c4-107">Hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="636c4-107">Property value</span></span>

`System.Data.SqlTypes.SqlStreamChars`\
<span data-ttu-id="636c4-108">Datového proudu znaků.</span><span class="sxs-lookup"><span data-stu-id="636c4-108">The character stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="636c4-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="636c4-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="636c4-110">`SqlChars.Stream` Vlastnost je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="636c4-110">The `SqlChars.Stream` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="636c4-111">Microsoft nepodporuje použití této vlastnosti v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="636c4-111">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="636c4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="636c4-112">Requirements</span></span>

<span data-ttu-id="636c4-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="636c4-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="636c4-114">**Sestavení:** System.Data (v System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="636c4-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="636c4-115">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="636c4-115">**.NET Framework versions:** Available since 2.0.</span></span>