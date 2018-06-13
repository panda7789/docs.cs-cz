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
ms.openlocfilehash: dcd7dc7c51caa94308760c0086384c8eea184ee9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443594"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="6087a-102">COUNINITIEE – výčet</span><span class="sxs-lookup"><span data-stu-id="6087a-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="6087a-103">Určuje konstanty používané [couninitializeee –](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) při inicializaci modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6087a-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6087a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6087a-104">Syntax</span></span>  
  
```  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,   
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="6087a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="6087a-105">Members</span></span>  
  
|<span data-ttu-id="6087a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="6087a-106">Member</span></span>|<span data-ttu-id="6087a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6087a-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="6087a-108">Určuje výchozí režim uninitialization.</span><span class="sxs-lookup"><span data-stu-id="6087a-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="6087a-109">Určuje režim uninitialization pro uvolnění sestavení.</span><span class="sxs-lookup"><span data-stu-id="6087a-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6087a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6087a-110">Requirements</span></span>  
 <span data-ttu-id="6087a-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6087a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6087a-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6087a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6087a-113">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6087a-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6087a-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6087a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6087a-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="6087a-115">See Also</span></span>  
 [<span data-ttu-id="6087a-116">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="6087a-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
