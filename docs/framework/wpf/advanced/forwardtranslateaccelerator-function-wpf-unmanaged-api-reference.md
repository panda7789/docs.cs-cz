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
ms.openlocfilehash: 4bb7e665bb836dc5f95b14f39179f1d4b9f8173d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080251"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="88534-102">Funkce ForwardTranslateAccelerator (WPF nespravovaná referenční dokumentace rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="88534-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="88534-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="88534-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="88534-104">Používá infrastrukturu Windows Presentation Foundation (WPF) pro správu systému windows.</span><span class="sxs-lookup"><span data-stu-id="88534-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88534-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88534-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="88534-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="88534-106">Parameters</span></span>  
 <span data-ttu-id="88534-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="88534-107">pMsg</span></span>  
 <span data-ttu-id="88534-108">Ukazatel na zprávu.</span><span class="sxs-lookup"><span data-stu-id="88534-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="88534-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="88534-109">appUnhandled</span></span>  
 <span data-ttu-id="88534-110">`true` Pokud už je zadaná příležitost dobře se zpracovala zpráva vstupní aplikace, ale nebyla zpracována. v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="88534-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88534-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="88534-111">Requirements</span></span>  
 <span data-ttu-id="88534-112">**Platformy:** Zobrazit [rozhraní .NET Framework System Requirements](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88534-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88534-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="88534-113">**DLL:**</span></span>  
  
 <span data-ttu-id="88534-114">V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="88534-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="88534-115">V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="88534-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="88534-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88534-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88534-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88534-117">See also</span></span>

- [<span data-ttu-id="88534-118">Odkaz na nespravované rozhraní API subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="88534-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
