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
ms.openlocfilehash: e5c3185dc6d488223d5882f543f0c690d82261b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402441"
---
# <a name="closeenum-method"></a><span data-ttu-id="1b9a9-102">CloseEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="1b9a9-102">CloseEnum Method</span></span>
<span data-ttu-id="1b9a9-103">Zavře uvedené výčtu a uvolní přidružené prostředky.</span><span class="sxs-lookup"><span data-stu-id="1b9a9-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b9a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b9a9-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b9a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1b9a9-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="1b9a9-106">Popisovač výčtu bude uzavřen.</span><span class="sxs-lookup"><span data-stu-id="1b9a9-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b9a9-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1b9a9-107">Return Value</span></span>  
 <span data-ttu-id="1b9a9-108">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="1b9a9-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b9a9-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1b9a9-109">Requirements</span></span>  
 <span data-ttu-id="1b9a9-110">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="1b9a9-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b9a9-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b9a9-111">See Also</span></span>  
 [<span data-ttu-id="1b9a9-112">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b9a9-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="1b9a9-113">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b9a9-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="1b9a9-114">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="1b9a9-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
