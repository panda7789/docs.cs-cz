---
title: Třída ServicePointManager. CloseConnectionGroups – metoda (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.CloseConnectionGroups
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: aae9a389ae35e249d43c9dc830a68ec32cf4afef
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990327"
---
# <a name="servicepointmanagercloseconnectiongroups-method"></a><span data-ttu-id="f5acc-102">Třída ServicePointManager. CloseConnectionGroups – metoda</span><span class="sxs-lookup"><span data-stu-id="f5acc-102">ServicePointManager.CloseConnectionGroups method</span></span>

<span data-ttu-id="f5acc-103">Projde všemi body služby a uzavře skupiny připojení, které mají zadaný název.</span><span class="sxs-lookup"><span data-stu-id="f5acc-103">Iterates through all service points and closes connection groups that have the specified name.</span></span>

```csharp
internal static void CloseConnectionGroups(string connectionGroupName)
```

> [!WARNING]
> <span data-ttu-id="f5acc-104">Tato metoda je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="f5acc-104">This method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f5acc-105">Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f5acc-105">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="f5acc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5acc-106">Parameters</span></span>

<span data-ttu-id="f5acc-107">`connectionGroupName` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f5acc-107">`connectionGroupName` <xref:System.String></span></span>

<span data-ttu-id="f5acc-108">Název skupiny připojení, která se má zavřít.</span><span class="sxs-lookup"><span data-stu-id="f5acc-108">The name of the connection group to close.</span></span>

## <a name="requirements"></a><span data-ttu-id="f5acc-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5acc-109">Requirements</span></span>

<span data-ttu-id="f5acc-110">**Obor názvů:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="f5acc-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="f5acc-111">**Sestavení:** Systém (v System.dll)</span><span class="sxs-lookup"><span data-stu-id="f5acc-111">**Assembly:** System (in System.dll)</span></span>
