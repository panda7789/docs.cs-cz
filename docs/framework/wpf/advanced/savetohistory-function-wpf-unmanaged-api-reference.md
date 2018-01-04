---
title: "Funkce SaveToHistory (WPF nespravované rozhraní API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: SaveToHistory
api_location: PresentationHost_v0400.dll
ms.assetid: 6dd101a3-44ad-4143-b228-772156f9b8ff
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af5294aad43b28bc590dd84466e133553f0ee47b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="savetohistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="e844b-102">Funkce SaveToHistory (WPF nespravované rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="e844b-102">SaveToHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="e844b-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="e844b-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="e844b-104">Používá infrastrukturu Windows Presentation Foundation (WPF) pro správu systému windows.</span><span class="sxs-lookup"><span data-stu-id="e844b-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e844b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e844b-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveToHistory(  
   __in_ecount(1) IStream* pHistoryStream  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e844b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e844b-106">Parameters</span></span>  
 <span data-ttu-id="e844b-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="e844b-107">pHistoryStream</span></span>  
 <span data-ttu-id="e844b-108">Ukazatel na datový proud historie.</span><span class="sxs-lookup"><span data-stu-id="e844b-108">A pointer to the history stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e844b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e844b-109">Requirements</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e844b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e844b-110">Requirements</span></span>  
 <span data-ttu-id="e844b-111">**Platformy:** najdete v části [požadavky na systém rozhraní .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e844b-111">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e844b-112">**KNIHOVNY DLL:**</span><span class="sxs-lookup"><span data-stu-id="e844b-112">**DLL:**</span></span>  
  
 <span data-ttu-id="e844b-113">V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="e844b-113">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="e844b-114">V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="e844b-114">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="e844b-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e844b-115">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e844b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e844b-116">See Also</span></span>  
 [<span data-ttu-id="e844b-117">Odkaz na nespravované rozhraní API subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="e844b-117">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
