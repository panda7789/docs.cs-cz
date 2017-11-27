---
title: "COINITIEE – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COINITIEE
api_location: mscoree.dll
api_type: COM
f1_keywords: COINITIEE
helpviewer_keywords: COINITIEE enumeration [.NET Framework metadata]
ms.assetid: 64264238-3b68-4bac-a887-36b552426a6c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 03711186954aa24beff65e5d4d5b5e484c6dc276
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="94b3c-102">COINITIEE – výčet</span><span class="sxs-lookup"><span data-stu-id="94b3c-102">COINITIEE Enumeration</span></span>
<span data-ttu-id="94b3c-103">Určuje konstanty používané [coinitializeee –](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) při inicializaci modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="94b3c-103">Specifies constants used by [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94b3c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94b3c-104">Syntax</span></span>  
  
```  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="94b3c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="94b3c-105">Members</span></span>  
  
|<span data-ttu-id="94b3c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="94b3c-106">Member</span></span>|<span data-ttu-id="94b3c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="94b3c-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="94b3c-108">Výchozí inicializace režim.</span><span class="sxs-lookup"><span data-stu-id="94b3c-108">Default initialization mode.</span></span> <span data-ttu-id="94b3c-109">To inicializuje modulu runtime a vytvoří výchozí <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="94b3c-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="94b3c-110">Inicializuje spustit spravovanou knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="94b3c-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="94b3c-111">Inicializuje ke spuštění spravované EXE.</span><span class="sxs-lookup"><span data-stu-id="94b3c-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="94b3c-112">To inicializuje modul runtime, ale nevytvoří výchozí <xref:System.AppDomain>, který je vytvořen po zadání rutinu EXE.</span><span class="sxs-lookup"><span data-stu-id="94b3c-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="94b3c-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="94b3c-113">Requirements</span></span>  
 <span data-ttu-id="94b3c-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94b3c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94b3c-115">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="94b3c-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="94b3c-116">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="94b3c-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="94b3c-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94b3c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94b3c-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="94b3c-118">See Also</span></span>  
 [<span data-ttu-id="94b3c-119">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="94b3c-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
