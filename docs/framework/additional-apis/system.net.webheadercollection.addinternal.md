---
title: WebHeaderCollection. AddInternal – metoda (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.WebHeaderCollection.AddInternal
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: fd7b13ccd1baad48ab99a85d80ccd6154651c608
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990322"
---
# <a name="webheadercollectionaddinternal-method"></a><span data-ttu-id="7d0a8-102">WebHeaderCollection. AddInternal – metoda</span><span class="sxs-lookup"><span data-stu-id="7d0a8-102">WebHeaderCollection.AddInternal method</span></span>

<span data-ttu-id="7d0a8-103">Přidá novou hlavičku se zadaným názvem a hodnotou do kolekce a obchází kontroly.</span><span class="sxs-lookup"><span data-stu-id="7d0a8-103">Adds a new header with the specified name and value to the collection, bypassing checks.</span></span>

```csharp
internal void AddInternal(string name, string value)
```

> [!WARNING]
> <span data-ttu-id="7d0a8-104">Tato metoda je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="7d0a8-104">This method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="7d0a8-105">Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7d0a8-105">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="7d0a8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d0a8-106">Parameters</span></span>

- <span data-ttu-id="7d0a8-107">`name` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="7d0a8-107">`name` <xref:System.String></span></span>

  <span data-ttu-id="7d0a8-108">Název záhlaví.</span><span class="sxs-lookup"><span data-stu-id="7d0a8-108">The name of the header.</span></span>

- <span data-ttu-id="7d0a8-109">`value` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="7d0a8-109">`value` <xref:System.String></span></span>

  <span data-ttu-id="7d0a8-110">Hodnota záhlaví</span><span class="sxs-lookup"><span data-stu-id="7d0a8-110">The value of the header.</span></span>

## <a name="requirements"></a><span data-ttu-id="7d0a8-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d0a8-111">Requirements</span></span>

<span data-ttu-id="7d0a8-112">**Obor názvů:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="7d0a8-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="7d0a8-113">**Sestavení:** Systém (v System.dll)</span><span class="sxs-lookup"><span data-stu-id="7d0a8-113">**Assembly:** System (in System.dll)</span></span>
