---
title: CloseEnum – metoda
ms.date: 03/30/2017
api_name:
- CloseEnum
- IALink.CloseEnum
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseEnum
helpviewer_keywords:
- CloseEnum method
ms.assetid: aa4a091e-13fe-4264-91de-e12f1c767c87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 145f92badf39b6456a82df8f7de23f1784d2ce50
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495738"
---
# <a name="closeenum-method"></a><span data-ttu-id="c894f-102">CloseEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="c894f-102">CloseEnum Method</span></span>
<span data-ttu-id="c894f-103">Zadaný výčet se zavře a uvolní přidružené prostředky.</span><span class="sxs-lookup"><span data-stu-id="c894f-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c894f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c894f-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c894f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c894f-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="c894f-106">Popisovač výčtu bude uzavřen.</span><span class="sxs-lookup"><span data-stu-id="c894f-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c894f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c894f-107">Return Value</span></span>  
 <span data-ttu-id="c894f-108">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="c894f-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c894f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c894f-109">Requirements</span></span>  
 <span data-ttu-id="c894f-110">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="c894f-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c894f-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c894f-111">See also</span></span>
- [<span data-ttu-id="c894f-112">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c894f-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="c894f-113">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c894f-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="c894f-114">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="c894f-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
