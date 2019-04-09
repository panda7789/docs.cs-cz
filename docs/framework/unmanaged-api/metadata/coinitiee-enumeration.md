---
title: COINITIEE – výčet
ms.date: 03/30/2017
api_name:
- COINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COINITIEE
helpviewer_keywords:
- COINITIEE enumeration [.NET Framework metadata]
ms.assetid: 64264238-3b68-4bac-a887-36b552426a6c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4a84fdfdba96c58671302c723b8a56848b70eb60
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180012"
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="2a429-102">COINITIEE – výčet</span><span class="sxs-lookup"><span data-stu-id="2a429-102">COINITIEE Enumeration</span></span>
<span data-ttu-id="2a429-103">Určuje konstanty používané [coinitializeee –](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) při inicializaci modulu common language runtime.</span><span class="sxs-lookup"><span data-stu-id="2a429-103">Specifies constants used by [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a429-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a429-104">Syntax</span></span>  
  
```  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="2a429-105">Členové</span><span class="sxs-lookup"><span data-stu-id="2a429-105">Members</span></span>  
  
|<span data-ttu-id="2a429-106">Člen</span><span class="sxs-lookup"><span data-stu-id="2a429-106">Member</span></span>|<span data-ttu-id="2a429-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2a429-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="2a429-108">Výchozí inicializace režim.</span><span class="sxs-lookup"><span data-stu-id="2a429-108">Default initialization mode.</span></span> <span data-ttu-id="2a429-109">To inicializuje modul runtime a vytvoří výchozí <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="2a429-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="2a429-110">Inicializuje ke spuštění spravované knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="2a429-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="2a429-111">Inicializuje pro spuštění spravovaného EXE.</span><span class="sxs-lookup"><span data-stu-id="2a429-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="2a429-112">To inicializuje modul runtime, ale nevytváří výchozí <xref:System.AppDomain>, který je vytvořen po zadání rutinu souboru EXE.</span><span class="sxs-lookup"><span data-stu-id="2a429-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2a429-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2a429-113">Requirements</span></span>  
 <span data-ttu-id="2a429-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a429-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a429-115">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2a429-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2a429-116">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2a429-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="2a429-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2a429-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2a429-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a429-118">See also</span></span>

- [<span data-ttu-id="2a429-119">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="2a429-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
