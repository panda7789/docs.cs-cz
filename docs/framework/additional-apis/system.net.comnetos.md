---
title: ComNetOS – třída (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ComNetOS
- System.Net.ComNetOS.IsWin7orLater
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ed2b970d07df2c338870b386e75c1688703f1d68
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990342"
---
# <a name="comnetos-class"></a><span data-ttu-id="e63ab-102">ComNetOS – třída</span><span class="sxs-lookup"><span data-stu-id="e63ab-102">ComNetOS class</span></span>

<span data-ttu-id="e63ab-103">Poskytuje informace o aktuálním operačním systému, jako je jeho verze a typ instalace (klient nebo Server).</span><span class="sxs-lookup"><span data-stu-id="e63ab-103">Provides information about the current operating system, such as its version and installation type (client or server).</span></span> <span data-ttu-id="e63ab-104">Tuto třídu nelze zdědit.</span><span class="sxs-lookup"><span data-stu-id="e63ab-104">This class cannot be inherited.</span></span>
  
```csharp  
internal static class ComNetOS
```

> [!WARNING]
> <span data-ttu-id="e63ab-105">Tato třída je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="e63ab-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="e63ab-106">Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e63ab-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="iswin7orlater-field"></a><span data-ttu-id="e63ab-107">Pole IsWin7orLater</span><span class="sxs-lookup"><span data-stu-id="e63ab-107">IsWin7orLater field</span></span>

<span data-ttu-id="e63ab-108">Určuje, jestli je verze operačního systému Windows 7 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="e63ab-108">Specifies whether the operating system version is Windows 7 or later.</span></span>

```csharp
internal static readonly bool IsWin7orLater
```

## <a name="requirements"></a><span data-ttu-id="e63ab-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e63ab-109">Requirements</span></span>

<span data-ttu-id="e63ab-110">**Obor názvů:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="e63ab-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="e63ab-111">**Sestavení:** Systém (v System.dll)</span><span class="sxs-lookup"><span data-stu-id="e63ab-111">**Assembly:** System (in System.dll)</span></span>
