---
title: "Funkce LoadFromHistory (WPF nespravované rozhraní API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: LoadFromHistory
api_location: PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cdb68700ab0c11bbd6b09b83a826dc5ca4faa086
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="be442-102">Funkce LoadFromHistory (WPF nespravované rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="be442-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="be442-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="be442-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="be442-104">Používá infrastrukturu Windows Presentation Foundation (WPF) pro správu systému windows.</span><span class="sxs-lookup"><span data-stu-id="be442-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be442-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be442-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be442-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="be442-106">Parameters</span></span>  
 <span data-ttu-id="be442-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="be442-107">pHistoryStream</span></span>  
 <span data-ttu-id="be442-108">Ukazatel na datový proud informace o historii.</span><span class="sxs-lookup"><span data-stu-id="be442-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="be442-109">pBindCtx</span><span class="sxs-lookup"><span data-stu-id="be442-109">pBindCtx</span></span>  
 <span data-ttu-id="be442-110">Ukazatel na kontext vazby.</span><span class="sxs-lookup"><span data-stu-id="be442-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be442-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be442-111">Requirements</span></span>  
 <span data-ttu-id="be442-112">**Platformy:** najdete v části [požadavky na systém rozhraní .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be442-112">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be442-113">**KNIHOVNY DLL:**</span><span class="sxs-lookup"><span data-stu-id="be442-113">**DLL:**</span></span>  
  
 <span data-ttu-id="be442-114">V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="be442-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="be442-115">V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="be442-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="be442-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be442-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be442-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="be442-117">See Also</span></span>  
 [<span data-ttu-id="be442-118">WPF nespravované rozhraní API</span><span class="sxs-lookup"><span data-stu-id="be442-118">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
