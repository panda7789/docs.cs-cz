---
title: Funkce LoadFromHistory – reference nespravovaného rozhraní API WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: 7807e073d1f09ac6a6213aee6d86d53cc75a3c56
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727927"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="8dc2e-102">LoadFromHistory – funkce (Referenční dokumentace rozhraní API nespravovaného subsystému WPF)</span><span class="sxs-lookup"><span data-stu-id="8dc2e-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="8dc2e-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určeno pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="8dc2e-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="8dc2e-104">Používá se v infrastruktuře Windows Presentation Foundation (WPF) pro správu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="8dc2e-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dc2e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8dc2e-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="8dc2e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dc2e-106">Parameters</span></span>  
 <span data-ttu-id="8dc2e-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="8dc2e-107">pHistoryStream</span></span>  
 <span data-ttu-id="8dc2e-108">Ukazatel na datový proud informací o historii.</span><span class="sxs-lookup"><span data-stu-id="8dc2e-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="8dc2e-109">pBindCtx</span><span class="sxs-lookup"><span data-stu-id="8dc2e-109">pBindCtx</span></span>  
 <span data-ttu-id="8dc2e-110">Ukazatel na kontext vazby.</span><span class="sxs-lookup"><span data-stu-id="8dc2e-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dc2e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8dc2e-111">Requirements</span></span>  
 <span data-ttu-id="8dc2e-112">**Platformy:** Viz [požadavky na systém .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8dc2e-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8dc2e-113">**DLL**</span><span class="sxs-lookup"><span data-stu-id="8dc2e-113">**DLL:**</span></span>  
  
 <span data-ttu-id="8dc2e-114">V .NET Framework 3,0 a 3,5: PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="8dc2e-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="8dc2e-115">V .NET Framework 4 a novější: PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="8dc2e-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="8dc2e-116">**Verze .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8dc2e-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dc2e-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="8dc2e-117">See also</span></span>

- [<span data-ttu-id="8dc2e-118">Odkaz na nespravované rozhraní API subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="8dc2e-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
