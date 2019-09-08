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
ms.openlocfilehash: 8d9529022eb04c81152dced5c63f255c510851a0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777472"
---
# <a name="closeenum-method"></a><span data-ttu-id="6b5c8-102">CloseEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="6b5c8-102">CloseEnum Method</span></span>
<span data-ttu-id="6b5c8-103">Zavře zadaný výčet a uvolní přidružené prostředky.</span><span class="sxs-lookup"><span data-stu-id="6b5c8-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b5c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b5c8-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b5c8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b5c8-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="6b5c8-106">Popisovač výčtu, který má být uzavřen.</span><span class="sxs-lookup"><span data-stu-id="6b5c8-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b5c8-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6b5c8-107">Return Value</span></span>  
 <span data-ttu-id="6b5c8-108">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="6b5c8-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b5c8-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6b5c8-109">Requirements</span></span>  
 <span data-ttu-id="6b5c8-110">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="6b5c8-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b5c8-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b5c8-111">See also</span></span>

- [<span data-ttu-id="6b5c8-112">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6b5c8-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="6b5c8-113">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6b5c8-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="6b5c8-114">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="6b5c8-114">ALink API</span></span>](index.md)
