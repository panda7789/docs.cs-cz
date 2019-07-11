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
ms.openlocfilehash: 3d8189365a73e85c0b9f5efb2aa03074385a3fb8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750743"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="1b1a9-102">COUNINITIEE – výčet</span><span class="sxs-lookup"><span data-stu-id="1b1a9-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="1b1a9-103">Určuje konstanty používané [couninitializeee –](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) při inicializaci modulu common language runtime.</span><span class="sxs-lookup"><span data-stu-id="1b1a9-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b1a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b1a9-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,   
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="1b1a9-105">Členové</span><span class="sxs-lookup"><span data-stu-id="1b1a9-105">Members</span></span>  
  
|<span data-ttu-id="1b1a9-106">Člen</span><span class="sxs-lookup"><span data-stu-id="1b1a9-106">Member</span></span>|<span data-ttu-id="1b1a9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1b1a9-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="1b1a9-108">Určuje výchozí režim rušení inicializace.</span><span class="sxs-lookup"><span data-stu-id="1b1a9-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="1b1a9-109">Určuje režim rušení inicializace pro uvolňování sestavení.</span><span class="sxs-lookup"><span data-stu-id="1b1a9-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1b1a9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1b1a9-110">Requirements</span></span>  
 <span data-ttu-id="1b1a9-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b1a9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b1a9-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1b1a9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1b1a9-113">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1b1a9-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1b1a9-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b1a9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b1a9-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1b1a9-115">See also</span></span>

- [<span data-ttu-id="1b1a9-116">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="1b1a9-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
