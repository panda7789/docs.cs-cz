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
ms.openlocfilehash: 9b6c839cc664105149f26b0d21d7ba7fb91b3e29
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742209"
---
# <a name="closeenum-method"></a><span data-ttu-id="32d26-102">CloseEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="32d26-102">CloseEnum Method</span></span>
<span data-ttu-id="32d26-103">Zadaný výčet se zavře a uvolní přidružené prostředky.</span><span class="sxs-lookup"><span data-stu-id="32d26-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32d26-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32d26-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="32d26-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32d26-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="32d26-106">Popisovač výčtu bude uzavřen.</span><span class="sxs-lookup"><span data-stu-id="32d26-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32d26-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="32d26-107">Return Value</span></span>  
 <span data-ttu-id="32d26-108">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="32d26-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32d26-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="32d26-109">Requirements</span></span>  
 <span data-ttu-id="32d26-110">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="32d26-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32d26-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32d26-111">See also</span></span>

- [<span data-ttu-id="32d26-112">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="32d26-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="32d26-113">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="32d26-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="32d26-114">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="32d26-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
