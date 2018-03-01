---
title: "CorNativeLinkFlags – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c8477ef13c53db6cc4de58c4e707a82e2ab7f650
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="aca21-102">CorNativeLinkFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="aca21-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="aca21-103">Poskytuje příznak hodnoty používané linkeru při propojování nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="aca21-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aca21-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aca21-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="aca21-105">Členové</span><span class="sxs-lookup"><span data-stu-id="aca21-105">Members</span></span>  
  
|<span data-ttu-id="aca21-106">Člen</span><span class="sxs-lookup"><span data-stu-id="aca21-106">Member</span></span>|<span data-ttu-id="aca21-107">Popis</span><span class="sxs-lookup"><span data-stu-id="aca21-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="aca21-108">Označuje žádné příznaky.</span><span class="sxs-lookup"><span data-stu-id="aca21-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="aca21-109">Označuje `setLastError` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="aca21-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="aca21-110">Označuje `nomangle` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="aca21-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="aca21-111">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="aca21-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aca21-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aca21-112">Requirements</span></span>  
 <span data-ttu-id="aca21-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aca21-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aca21-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="aca21-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aca21-115">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aca21-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aca21-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aca21-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aca21-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="aca21-117">See Also</span></span>  
 [<span data-ttu-id="aca21-118">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="aca21-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
