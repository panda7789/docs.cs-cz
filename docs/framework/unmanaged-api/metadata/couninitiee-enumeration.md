---
title: COUNINITIEE – výčet
ms.date: 03/30/2017
api_name:
- COUNINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COUNINITIEE
helpviewer_keywords:
- COUNINITIEE enumeration [.NET Framework metadata]
ms.assetid: c42baa79-f469-4330-95a2-baf7f021c2fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0cf1bfa03fd14d6324af60781003a8072a267a7e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102944"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="f2565-102">COUNINITIEE – výčet</span><span class="sxs-lookup"><span data-stu-id="f2565-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="f2565-103">Určuje konstanty používané [couninitializeee –](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) při inicializaci modulu common language runtime.</span><span class="sxs-lookup"><span data-stu-id="f2565-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2565-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2565-104">Syntax</span></span>  
  
```  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,   
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="f2565-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f2565-105">Members</span></span>  
  
|<span data-ttu-id="f2565-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f2565-106">Member</span></span>|<span data-ttu-id="f2565-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f2565-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="f2565-108">Určuje výchozí režim rušení inicializace.</span><span class="sxs-lookup"><span data-stu-id="f2565-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="f2565-109">Určuje režim rušení inicializace pro uvolňování sestavení.</span><span class="sxs-lookup"><span data-stu-id="f2565-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f2565-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f2565-110">Requirements</span></span>  
 <span data-ttu-id="f2565-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2565-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2565-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f2565-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f2565-113">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f2565-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="f2565-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f2565-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f2565-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2565-115">See also</span></span>

- [<span data-ttu-id="f2565-116">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="f2565-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
