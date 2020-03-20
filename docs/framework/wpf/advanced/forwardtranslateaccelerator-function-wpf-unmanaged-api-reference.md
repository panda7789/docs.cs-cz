---
title: Funkce ForwardTranslateAccelerator – nespravovaný odkaz rozhraní API WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: a0a01be3000dc53df7855cb74015ba1164206838
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186622"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="3e5cf-102">Funkce ForwardTranslateAccelerator (WPF Unmanaged API Reference)</span><span class="sxs-lookup"><span data-stu-id="3e5cf-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="3e5cf-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určeno k použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="3e5cf-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="3e5cf-104">Používá infrastrukturu WPF (Windows Presentation Foundation) pro správu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="3e5cf-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e5cf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e5cf-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e5cf-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e5cf-106">Parameters</span></span>  
 <span data-ttu-id="3e5cf-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="3e5cf-107">pMsg</span></span>  
 <span data-ttu-id="3e5cf-108">Ukazatel na zprávu.</span><span class="sxs-lookup"><span data-stu-id="3e5cf-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="3e5cf-109">appNeošetřeno</span><span class="sxs-lookup"><span data-stu-id="3e5cf-109">appUnhandled</span></span>  
 <span data-ttu-id="3e5cf-110">`true`když aplikace již byla dána možnost zpracovat vstupní zprávu, ale nezpracoval ji; v `false`opačném případě .</span><span class="sxs-lookup"><span data-stu-id="3e5cf-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e5cf-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e5cf-111">Requirements</span></span>  
 <span data-ttu-id="3e5cf-112">**Platformy:** Viz [Požadavky na systém rozhraní .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e5cf-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e5cf-113">**Knihovny dll:**</span><span class="sxs-lookup"><span data-stu-id="3e5cf-113">**DLL:**</span></span>  
  
 <span data-ttu-id="3e5cf-114">V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll ll</span><span class="sxs-lookup"><span data-stu-id="3e5cf-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="3e5cf-115">V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="3e5cf-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="3e5cf-116">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e5cf-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e5cf-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e5cf-117">See also</span></span>

- [<span data-ttu-id="3e5cf-118">Referenční informace k nespravovanému rozhraní API WPF</span><span class="sxs-lookup"><span data-stu-id="3e5cf-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
