---
title: Funkce ForwardTranslateAccelerator – reference nespravovaného rozhraní API WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: f6e8208ffe2c186234f30f31e346ca6b1d0be4c0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747046"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="7f919-102">ForwardTranslateAccelerator – funkce (Referenční dokumentace rozhraní API nespravovaného subsystému WPF)</span><span class="sxs-lookup"><span data-stu-id="7f919-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="7f919-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určeno pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="7f919-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="7f919-104">Používá se v infrastruktuře Windows Presentation Foundation (WPF) pro správu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7f919-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f919-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f919-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f919-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f919-106">Parameters</span></span>  
 <span data-ttu-id="7f919-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="7f919-107">pMsg</span></span>  
 <span data-ttu-id="7f919-108">Ukazatel na zprávu.</span><span class="sxs-lookup"><span data-stu-id="7f919-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="7f919-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="7f919-109">appUnhandled</span></span>  
 <span data-ttu-id="7f919-110">`true` v případě, že se aplikaci již dostala možnost zpracovat vstupní zprávu, ale ji nezpracovala; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="7f919-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f919-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f919-111">Requirements</span></span>  
 <span data-ttu-id="7f919-112">**Platformy:** Viz [požadavky na systém .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f919-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f919-113">**DLL**</span><span class="sxs-lookup"><span data-stu-id="7f919-113">**DLL:**</span></span>  
  
 <span data-ttu-id="7f919-114">V .NET Framework 3,0 a 3,5: PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="7f919-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="7f919-115">V .NET Framework 4 a novější: PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="7f919-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="7f919-116">**Verze .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f919-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f919-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f919-117">See also</span></span>

- [<span data-ttu-id="7f919-118">Odkaz na nespravované rozhraní API subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="7f919-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
