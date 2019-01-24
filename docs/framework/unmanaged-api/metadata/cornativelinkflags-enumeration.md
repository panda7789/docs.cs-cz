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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf0fdb1e46bfbd17505e255d539547a00eb4764c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694552"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="6ed57-102">CorNativeLinkFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="6ed57-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="6ed57-103">Obsahuje příznak hodnoty používané linkeru při propojování nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="6ed57-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ed57-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ed57-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="6ed57-105">Členové</span><span class="sxs-lookup"><span data-stu-id="6ed57-105">Members</span></span>  
  
|<span data-ttu-id="6ed57-106">Člen</span><span class="sxs-lookup"><span data-stu-id="6ed57-106">Member</span></span>|<span data-ttu-id="6ed57-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6ed57-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="6ed57-108">Označuje žádné příznaky.</span><span class="sxs-lookup"><span data-stu-id="6ed57-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="6ed57-109">Označuje `setLastError` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="6ed57-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="6ed57-110">Označuje `nomangle` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="6ed57-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="6ed57-111">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="6ed57-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6ed57-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6ed57-112">Requirements</span></span>  
 <span data-ttu-id="6ed57-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ed57-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ed57-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6ed57-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6ed57-115">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6ed57-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6ed57-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ed57-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ed57-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ed57-117">See also</span></span>
- [<span data-ttu-id="6ed57-118">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="6ed57-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
