---
title: "Funkce ForwardTranslateAccelerator (WPF nespravované rozhraní API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: ForwardTranslateAccelerator
api_location: PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 663b28ed1a9430a6280ccd0ee9a44da2dea0c3cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="b77c3-102">Funkce ForwardTranslateAccelerator (WPF nespravované rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="b77c3-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="b77c3-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="b77c3-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="b77c3-104">Používá infrastrukturu Windows Presentation Foundation (WPF) pro správu systému windows.</span><span class="sxs-lookup"><span data-stu-id="b77c3-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b77c3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b77c3-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b77c3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b77c3-106">Parameters</span></span>  
 <span data-ttu-id="b77c3-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="b77c3-107">pMsg</span></span>  
 <span data-ttu-id="b77c3-108">Ukazatel na zprávu.</span><span class="sxs-lookup"><span data-stu-id="b77c3-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="b77c3-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="b77c3-109">appUnhandled</span></span>  
 <span data-ttu-id="b77c3-110">`true`Při aplikaci již nebyla zadána možnost zpracovat vstupní zprávy, ale nebyla zpracována. v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="b77c3-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b77c3-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b77c3-111">Requirements</span></span>  
 <span data-ttu-id="b77c3-112">**Platformy:** najdete v části [požadavky na systém rozhraní .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b77c3-112">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b77c3-113">**KNIHOVNY DLL:**</span><span class="sxs-lookup"><span data-stu-id="b77c3-113">**DLL:**</span></span>  
  
 <span data-ttu-id="b77c3-114">V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="b77c3-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="b77c3-115">V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="b77c3-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="b77c3-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b77c3-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b77c3-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="b77c3-117">See Also</span></span>  
 [<span data-ttu-id="b77c3-118">WPF nespravované rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b77c3-118">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
