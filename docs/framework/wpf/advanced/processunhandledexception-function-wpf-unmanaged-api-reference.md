---
title: Funkce ProcessUnhandledException (WPF nespravovaná referenční dokumentace rozhraní API)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: 73480f7cd8be7bcb5296782a8503eb689442a14c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54578637"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="43f2e-102">Funkce ProcessUnhandledException (WPF nespravovaná referenční dokumentace rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="43f2e-102">ProcessUnhandledException Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="43f2e-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="43f2e-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="43f2e-104">Používá infrastrukturu Windows Presentation Foundation (WPF) pro zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="43f2e-104">Used by the Windows Presentation Foundation (WPF) infrastructure for exception handling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43f2e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43f2e-105">Syntax</span></span>  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="43f2e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="43f2e-106">Parameters</span></span>  
 <span data-ttu-id="43f2e-107">errorMsg</span><span class="sxs-lookup"><span data-stu-id="43f2e-107">errorMsg</span></span>  
 <span data-ttu-id="43f2e-108">Chybová zpráva</span><span class="sxs-lookup"><span data-stu-id="43f2e-108">The error message.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43f2e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="43f2e-109">Requirements</span></span>  
 <span data-ttu-id="43f2e-110">**Platformy:** Zobrazit [rozhraní .NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43f2e-110">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43f2e-111">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="43f2e-111">**DLL:**</span></span>  
  
 <span data-ttu-id="43f2e-112">V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="43f2e-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="43f2e-113">V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="43f2e-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="43f2e-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43f2e-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43f2e-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43f2e-115">See also</span></span>
- [<span data-ttu-id="43f2e-116">Odkaz na nespravované rozhraní API subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="43f2e-116">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
