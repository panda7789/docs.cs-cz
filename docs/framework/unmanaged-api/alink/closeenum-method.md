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
ms.openlocfilehash: 018af6929ad4023c70bfb975b9be010912415dd7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446558"
---
# <a name="closeenum-method"></a><span data-ttu-id="3e16e-102">CloseEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="3e16e-102">CloseEnum Method</span></span>
<span data-ttu-id="3e16e-103">Closes the indicated enumeration and frees associated resources.</span><span class="sxs-lookup"><span data-stu-id="3e16e-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e16e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e16e-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e16e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e16e-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="3e16e-106">Handle of enumeration to be closed.</span><span class="sxs-lookup"><span data-stu-id="3e16e-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e16e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3e16e-107">Return Value</span></span>  
 <span data-ttu-id="3e16e-108">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="3e16e-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e16e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e16e-109">Requirements</span></span>  
 <span data-ttu-id="3e16e-110">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="3e16e-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e16e-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e16e-111">See also</span></span>

- [<span data-ttu-id="3e16e-112">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e16e-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="3e16e-113">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e16e-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="3e16e-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="3e16e-114">ALink API</span></span>](index.md)
