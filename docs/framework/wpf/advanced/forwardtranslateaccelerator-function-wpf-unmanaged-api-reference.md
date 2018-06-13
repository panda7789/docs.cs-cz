---
title: Funkce ForwardTranslateAccelerator (WPF nespravované rozhraní API)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: d8a296c0590d07c4929610021714d2a257236d67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542558"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="d2ac9-102">Funkce ForwardTranslateAccelerator (WPF nespravované rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="d2ac9-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="d2ac9-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="d2ac9-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="d2ac9-104">Používá infrastrukturu Windows Presentation Foundation (WPF) pro správu systému windows.</span><span class="sxs-lookup"><span data-stu-id="d2ac9-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2ac9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2ac9-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d2ac9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2ac9-106">Parameters</span></span>  
 <span data-ttu-id="d2ac9-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="d2ac9-107">pMsg</span></span>  
 <span data-ttu-id="d2ac9-108">Ukazatel na zprávu.</span><span class="sxs-lookup"><span data-stu-id="d2ac9-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="d2ac9-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="d2ac9-109">appUnhandled</span></span>  
 <span data-ttu-id="d2ac9-110">`true` Při aplikaci již nebyla zadána možnost zpracovat vstupní zprávy, ale nebyla zpracována. v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="d2ac9-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2ac9-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2ac9-111">Requirements</span></span>  
 <span data-ttu-id="d2ac9-112">**Platformy:** najdete v části [požadavky na systém rozhraní .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2ac9-112">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2ac9-113">**KNIHOVNY DLL:**</span><span class="sxs-lookup"><span data-stu-id="d2ac9-113">**DLL:**</span></span>  
  
 <span data-ttu-id="d2ac9-114">V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="d2ac9-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="d2ac9-115">V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="d2ac9-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="d2ac9-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2ac9-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2ac9-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2ac9-117">See Also</span></span>  
 [<span data-ttu-id="d2ac9-118">Odkaz na nespravované rozhraní API subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="d2ac9-118">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
