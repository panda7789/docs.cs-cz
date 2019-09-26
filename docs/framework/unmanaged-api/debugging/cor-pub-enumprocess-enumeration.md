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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eab5fc13b74d8af4f0baaa3953c5c73ea255bfe6
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274023"
---
# <a name="cor_pub_enumprocess-enumeration"></a><span data-ttu-id="faf9f-102">COR_PUB_ENUMPROCESS – výčet</span><span class="sxs-lookup"><span data-stu-id="faf9f-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="faf9f-103">Určuje typ procesu, který se má vyčíslit.</span><span class="sxs-lookup"><span data-stu-id="faf9f-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faf9f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="faf9f-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="faf9f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="faf9f-105">Members</span></span>  
  
|<span data-ttu-id="faf9f-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="faf9f-106">Member name</span></span>|<span data-ttu-id="faf9f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="faf9f-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="faf9f-108">Spravovaný proces.</span><span class="sxs-lookup"><span data-stu-id="faf9f-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="faf9f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="faf9f-109">Remarks</span></span>  
 <span data-ttu-id="faf9f-110">Aktuální verze nespravovaného ladicího rozhraní API vytváří výčet pouze spravovaných procesů.</span><span class="sxs-lookup"><span data-stu-id="faf9f-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faf9f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="faf9f-111">Requirements</span></span>  
 <span data-ttu-id="faf9f-112">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faf9f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faf9f-113">**Hlaviček** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="faf9f-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="faf9f-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="faf9f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="faf9f-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faf9f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faf9f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="faf9f-116">See also</span></span>

- [<span data-ttu-id="faf9f-117">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="faf9f-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
