---
title: Funkce LoadFromHistory (WPF nespravovaná referenční dokumentace rozhraní API)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: 155b83b8b904350bd6faf73ea21d1db4f83085b7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376127"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="27d9d-102">Funkce LoadFromHistory (WPF nespravovaná referenční dokumentace rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="27d9d-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="27d9d-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="27d9d-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="27d9d-104">Používá infrastrukturu Windows Presentation Foundation (WPF) pro správu systému windows.</span><span class="sxs-lookup"><span data-stu-id="27d9d-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27d9d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27d9d-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27d9d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="27d9d-106">Parameters</span></span>  
 <span data-ttu-id="27d9d-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="27d9d-107">pHistoryStream</span></span>  
 <span data-ttu-id="27d9d-108">Ukazatel na datový proud informace o historii.</span><span class="sxs-lookup"><span data-stu-id="27d9d-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="27d9d-109">pBindCtx</span><span class="sxs-lookup"><span data-stu-id="27d9d-109">pBindCtx</span></span>  
 <span data-ttu-id="27d9d-110">Ukazatel do kontextu vazby.</span><span class="sxs-lookup"><span data-stu-id="27d9d-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27d9d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="27d9d-111">Requirements</span></span>  
 <span data-ttu-id="27d9d-112">**Platformy:** Zobrazit [rozhraní .NET Framework System Requirements](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27d9d-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27d9d-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="27d9d-113">**DLL:**</span></span>  
  
 <span data-ttu-id="27d9d-114">V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="27d9d-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="27d9d-115">V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="27d9d-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="27d9d-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27d9d-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27d9d-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27d9d-117">See also</span></span>
- [<span data-ttu-id="27d9d-118">Odkaz na nespravované rozhraní API subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="27d9d-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
