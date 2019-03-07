---
title: Funkce ForwardTranslateAccelerator (WPF nespravovaná referenční dokumentace rozhraní API)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: 2b1914b9a0e478c7ab15fca77b7df952123153ac
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502281"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="c9b42-102">Funkce ForwardTranslateAccelerator (WPF nespravovaná referenční dokumentace rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="c9b42-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="c9b42-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="c9b42-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="c9b42-104">Používá infrastrukturu Windows Presentation Foundation (WPF) pro správu systému windows.</span><span class="sxs-lookup"><span data-stu-id="c9b42-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9b42-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9b42-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9b42-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9b42-106">Parameters</span></span>  
 <span data-ttu-id="c9b42-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="c9b42-107">pMsg</span></span>  
 <span data-ttu-id="c9b42-108">Ukazatel na zprávu.</span><span class="sxs-lookup"><span data-stu-id="c9b42-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="c9b42-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="c9b42-109">appUnhandled</span></span>  
 <span data-ttu-id="c9b42-110">`true` Pokud už je zadaná příležitost dobře se zpracovala zpráva vstupní aplikace, ale nebyla zpracována. v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="c9b42-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9b42-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9b42-111">Requirements</span></span>  
 <span data-ttu-id="c9b42-112">**Platformy:** Zobrazit [rozhraní .NET Framework System Requirements](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9b42-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9b42-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="c9b42-113">**DLL:**</span></span>  
  
 <span data-ttu-id="c9b42-114">V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="c9b42-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="c9b42-115">V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="c9b42-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="c9b42-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9b42-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9b42-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9b42-117">See also</span></span>
- [<span data-ttu-id="c9b42-118">Odkaz na nespravované rozhraní API subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="c9b42-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
