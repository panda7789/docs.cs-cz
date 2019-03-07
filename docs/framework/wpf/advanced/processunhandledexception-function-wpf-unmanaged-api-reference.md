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
ms.openlocfilehash: 3a95e8e68361f060d843247f400043a79dc28889
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466862"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="9afcc-102">Funkce ProcessUnhandledException (WPF nespravovaná referenční dokumentace rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="9afcc-102">ProcessUnhandledException Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="9afcc-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="9afcc-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="9afcc-104">Používá infrastrukturu Windows Presentation Foundation (WPF) pro zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="9afcc-104">Used by the Windows Presentation Foundation (WPF) infrastructure for exception handling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9afcc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9afcc-105">Syntax</span></span>  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="9afcc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9afcc-106">Parameters</span></span>  
 <span data-ttu-id="9afcc-107">errorMsg</span><span class="sxs-lookup"><span data-stu-id="9afcc-107">errorMsg</span></span>  
 <span data-ttu-id="9afcc-108">Chybová zpráva</span><span class="sxs-lookup"><span data-stu-id="9afcc-108">The error message.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9afcc-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9afcc-109">Requirements</span></span>  
 <span data-ttu-id="9afcc-110">**Platformy:** Zobrazit [rozhraní .NET Framework System Requirements](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9afcc-110">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9afcc-111">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="9afcc-111">**DLL:**</span></span>  
  
 <span data-ttu-id="9afcc-112">V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="9afcc-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="9afcc-113">V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="9afcc-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="9afcc-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9afcc-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9afcc-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9afcc-115">See also</span></span>
- [<span data-ttu-id="9afcc-116">Odkaz na nespravované rozhraní API subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="9afcc-116">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
