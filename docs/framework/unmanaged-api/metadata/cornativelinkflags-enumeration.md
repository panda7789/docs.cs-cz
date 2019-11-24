---
title: CorNativeLinkFlags – výčet
ms.date: 03/30/2017
api_name:
- CorNativeLinkFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkFlags
helpviewer_keywords:
- CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type:
- apiref
ms.openlocfilehash: 1362efbf518310240ce665badc93810d1c0b9b89
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450186"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="0b900-102">CorNativeLinkFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="0b900-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="0b900-103">Provides flag values used by the linker when linking native code.</span><span class="sxs-lookup"><span data-stu-id="0b900-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b900-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b900-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="0b900-105">Členové</span><span class="sxs-lookup"><span data-stu-id="0b900-105">Members</span></span>  
  
|<span data-ttu-id="0b900-106">Člen</span><span class="sxs-lookup"><span data-stu-id="0b900-106">Member</span></span>|<span data-ttu-id="0b900-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0b900-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="0b900-108">Indicates no flags.</span><span class="sxs-lookup"><span data-stu-id="0b900-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="0b900-109">Indicates a `setLastError` keyword.</span><span class="sxs-lookup"><span data-stu-id="0b900-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="0b900-110">Indicates a `nomangle` keyword.</span><span class="sxs-lookup"><span data-stu-id="0b900-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="0b900-111">Not used.</span><span class="sxs-lookup"><span data-stu-id="0b900-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0b900-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0b900-112">Requirements</span></span>  
 <span data-ttu-id="0b900-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b900-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b900-114">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0b900-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0b900-115">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0b900-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0b900-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b900-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b900-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b900-117">See also</span></span>

- [<span data-ttu-id="0b900-118">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="0b900-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
