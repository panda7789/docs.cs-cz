---
title: COR_PUB_ENUMPROCESS – výčet
ms.date: 03/30/2017
api_name:
- COR_PUB_ENUMPROCESS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_PUB_ENUMPROCESS
helpviewer_keywords:
- COR_PUB_ENUMPROCESS enumeration [.NET Framework debugging]
ms.assetid: 5d3ada6e-feea-47da-a7ed-b664107c137f
topic_type:
- apiref
ms.openlocfilehash: f789105751ae2d498740ab60f326f9c0597483b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099201"
---
# <a name="cor_pub_enumprocess-enumeration"></a><span data-ttu-id="df3fc-102">COR_PUB_ENUMPROCESS – výčet</span><span class="sxs-lookup"><span data-stu-id="df3fc-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="df3fc-103">Určuje typ procesu, který se má vyčíslit.</span><span class="sxs-lookup"><span data-stu-id="df3fc-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df3fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df3fc-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="df3fc-105">Členové</span><span class="sxs-lookup"><span data-stu-id="df3fc-105">Members</span></span>  
  
|<span data-ttu-id="df3fc-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="df3fc-106">Member name</span></span>|<span data-ttu-id="df3fc-107">Popis</span><span class="sxs-lookup"><span data-stu-id="df3fc-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="df3fc-108">Spravovaný proces.</span><span class="sxs-lookup"><span data-stu-id="df3fc-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df3fc-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="df3fc-109">Remarks</span></span>  
 <span data-ttu-id="df3fc-110">Aktuální verze nespravovaného ladicího rozhraní API vytváří výčet pouze spravovaných procesů.</span><span class="sxs-lookup"><span data-stu-id="df3fc-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df3fc-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="df3fc-111">Requirements</span></span>  
 <span data-ttu-id="df3fc-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df3fc-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df3fc-113">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="df3fc-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="df3fc-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="df3fc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df3fc-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df3fc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df3fc-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="df3fc-116">See also</span></span>

- [<span data-ttu-id="df3fc-117">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="df3fc-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
