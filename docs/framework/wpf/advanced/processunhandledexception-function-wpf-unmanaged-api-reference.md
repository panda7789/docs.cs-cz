---
title: Funkce ProcessUnhandledException – reference nespravovaného rozhraní API WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: 757e5ac3aa2dc4c87b210b026998523bd82045c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743917"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="6c625-102">ProcessUnhandledException – funkce (Referenční dokumentace rozhraní API nespravovaného subsystému WPF)</span><span class="sxs-lookup"><span data-stu-id="6c625-102">ProcessUnhandledException Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="6c625-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určeno pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="6c625-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="6c625-104">Používá se v infrastruktuře Windows Presentation Foundation (WPF) pro zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="6c625-104">Used by the Windows Presentation Foundation (WPF) infrastructure for exception handling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c625-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c625-105">Syntax</span></span>  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c625-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c625-106">Parameters</span></span>  
 <span data-ttu-id="6c625-107">errorMsg</span><span class="sxs-lookup"><span data-stu-id="6c625-107">errorMsg</span></span>  
 <span data-ttu-id="6c625-108">Chybová zpráva</span><span class="sxs-lookup"><span data-stu-id="6c625-108">The error message.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c625-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6c625-109">Requirements</span></span>  
 <span data-ttu-id="6c625-110">**Platformy:** Viz [požadavky na systém .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c625-110">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c625-111">**DLL**</span><span class="sxs-lookup"><span data-stu-id="6c625-111">**DLL:**</span></span>  
  
 <span data-ttu-id="6c625-112">V .NET Framework 3,0 a 3,5: PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="6c625-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="6c625-113">V .NET Framework 4 a novější: PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="6c625-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="6c625-114">**Verze .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c625-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c625-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c625-115">See also</span></span>

- [<span data-ttu-id="6c625-116">Odkaz na nespravované rozhraní API subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="6c625-116">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
