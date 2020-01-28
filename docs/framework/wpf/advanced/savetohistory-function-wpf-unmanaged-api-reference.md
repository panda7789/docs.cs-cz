---
title: Funkce SaveToHistory – reference nespravovaného rozhraní API WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- SaveToHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: 6dd101a3-44ad-4143-b228-772156f9b8ff
ms.openlocfilehash: 7337e5dc23a3dce5de8270902bce228c49bc6edb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731759"
---
# <a name="savetohistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="9c9b0-102">SaveToHistory – funkce (Referenční dokumentace rozhraní API nespravovaného subsystému WPF)</span><span class="sxs-lookup"><span data-stu-id="9c9b0-102">SaveToHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="9c9b0-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určeno pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="9c9b0-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="9c9b0-104">Používá se v infrastruktuře Windows Presentation Foundation (WPF) pro správu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9c9b0-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c9b0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c9b0-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveToHistory(  
   __in_ecount(1) IStream* pHistoryStream  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c9b0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c9b0-106">Parameters</span></span>  
 <span data-ttu-id="9c9b0-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="9c9b0-107">pHistoryStream</span></span>  
 <span data-ttu-id="9c9b0-108">Ukazatel na datový proud historie.</span><span class="sxs-lookup"><span data-stu-id="9c9b0-108">A pointer to the history stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c9b0-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9c9b0-109">Requirements</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c9b0-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9c9b0-110">Requirements</span></span>  
 <span data-ttu-id="9c9b0-111">**Platformy:** Viz [požadavky na systém .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c9b0-111">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c9b0-112">**DLL**</span><span class="sxs-lookup"><span data-stu-id="9c9b0-112">**DLL:**</span></span>  
  
 <span data-ttu-id="9c9b0-113">V .NET Framework 3,0 a 3,5: PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="9c9b0-113">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="9c9b0-114">V .NET Framework 4 a novější: PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="9c9b0-114">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="9c9b0-115">**Verze .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c9b0-115">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c9b0-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9c9b0-116">See also</span></span>

- [<span data-ttu-id="9c9b0-117">Odkaz na nespravované rozhraní API subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="9c9b0-117">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
