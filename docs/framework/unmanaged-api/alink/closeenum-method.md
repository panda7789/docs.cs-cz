---
title: "CloseEnum – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CloseEnum
- IALink.CloseEnum
api_location: alink.dll
api_type: COM
f1_keywords: CloseEnum
helpviewer_keywords: CloseEnum method
ms.assetid: aa4a091e-13fe-4264-91de-e12f1c767c87
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6ade939969069fb35221d83f8c7e4e380e903a00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="closeenum-method"></a><span data-ttu-id="e5e56-102">CloseEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="e5e56-102">CloseEnum Method</span></span>
<span data-ttu-id="e5e56-103">Zavře uvedené výčtu a uvolní přidružené prostředky.</span><span class="sxs-lookup"><span data-stu-id="e5e56-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5e56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5e56-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e5e56-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5e56-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="e5e56-106">Popisovač výčtu bude uzavřen.</span><span class="sxs-lookup"><span data-stu-id="e5e56-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5e56-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e5e56-107">Return Value</span></span>  
 <span data-ttu-id="e5e56-108">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="e5e56-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5e56-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5e56-109">Requirements</span></span>  
 <span data-ttu-id="e5e56-110">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="e5e56-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5e56-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5e56-111">See Also</span></span>  
 [<span data-ttu-id="e5e56-112">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5e56-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="e5e56-113">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5e56-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="e5e56-114">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="e5e56-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
