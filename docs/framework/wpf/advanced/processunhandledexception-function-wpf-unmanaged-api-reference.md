---
title: "Funkce ProcessUnhandledException (WPF nespravované rozhraní API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: ProcessUnhandledException
api_location: PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8328ae4bcbff54743e8df0a4b6ff6da3065ea470
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="48b95-102">Funkce ProcessUnhandledException (WPF nespravované rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="48b95-102">ProcessUnhandledException Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="48b95-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="48b95-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="48b95-104">Používá infrastrukturu Windows Presentation Foundation (WPF) pro zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="48b95-104">Used by the Windows Presentation Foundation (WPF) infrastructure for exception handling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48b95-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48b95-105">Syntax</span></span>  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48b95-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="48b95-106">Parameters</span></span>  
 <span data-ttu-id="48b95-107">errorMsg</span><span class="sxs-lookup"><span data-stu-id="48b95-107">errorMsg</span></span>  
 <span data-ttu-id="48b95-108">Chybová zpráva</span><span class="sxs-lookup"><span data-stu-id="48b95-108">The error message.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48b95-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="48b95-109">Requirements</span></span>  
 <span data-ttu-id="48b95-110">**Platformy:** najdete v části [požadavky na systém rozhraní .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48b95-110">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48b95-111">**KNIHOVNY DLL:**</span><span class="sxs-lookup"><span data-stu-id="48b95-111">**DLL:**</span></span>  
  
 <span data-ttu-id="48b95-112">V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="48b95-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="48b95-113">V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="48b95-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="48b95-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48b95-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48b95-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="48b95-115">See Also</span></span>  
 [<span data-ttu-id="48b95-116">WPF nespravované rozhraní API</span><span class="sxs-lookup"><span data-stu-id="48b95-116">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
