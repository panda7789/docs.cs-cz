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
ms.openlocfilehash: 02d5d23ec44d9fb7a244fc635ac174cf81ead173
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362185"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="bca06-102">Funkce ForwardTranslateAccelerator (WPF nespravovaná referenční dokumentace rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="bca06-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="bca06-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="bca06-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="bca06-104">Používá infrastrukturu Windows Presentation Foundation (WPF) pro správu systému windows.</span><span class="sxs-lookup"><span data-stu-id="bca06-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bca06-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bca06-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bca06-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bca06-106">Parameters</span></span>  
 <span data-ttu-id="bca06-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="bca06-107">pMsg</span></span>  
 <span data-ttu-id="bca06-108">Ukazatel na zprávu.</span><span class="sxs-lookup"><span data-stu-id="bca06-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="bca06-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="bca06-109">appUnhandled</span></span>  
 <span data-ttu-id="bca06-110">`true` Pokud už je zadaná příležitost dobře se zpracovala zpráva vstupní aplikace, ale nebyla zpracována. v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="bca06-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bca06-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bca06-111">Requirements</span></span>  
 <span data-ttu-id="bca06-112">**Platformy:** Zobrazit [rozhraní .NET Framework System Requirements](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bca06-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bca06-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="bca06-113">**DLL:**</span></span>  
  
 <span data-ttu-id="bca06-114">V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="bca06-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="bca06-115">V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="bca06-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="bca06-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bca06-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca06-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bca06-117">See also</span></span>
- [<span data-ttu-id="bca06-118">Odkaz na nespravované rozhraní API subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="bca06-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
