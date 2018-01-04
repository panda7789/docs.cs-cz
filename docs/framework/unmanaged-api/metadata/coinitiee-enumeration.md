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
ms.workload: dotnet
ms.openlocfilehash: ad117c3efd31cc176281e571b7fde11229c097e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="8e839-102">COINITIEE – výčet</span><span class="sxs-lookup"><span data-stu-id="8e839-102">COINITIEE Enumeration</span></span>
<span data-ttu-id="8e839-103">Určuje konstanty používané [coinitializeee –](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) při inicializaci modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="8e839-103">Specifies constants used by [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e839-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e839-104">Syntax</span></span>  
  
```  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="8e839-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8e839-105">Members</span></span>  
  
|<span data-ttu-id="8e839-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8e839-106">Member</span></span>|<span data-ttu-id="8e839-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8e839-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="8e839-108">Výchozí inicializace režim.</span><span class="sxs-lookup"><span data-stu-id="8e839-108">Default initialization mode.</span></span> <span data-ttu-id="8e839-109">To inicializuje modulu runtime a vytvoří výchozí <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="8e839-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="8e839-110">Inicializuje spustit spravovanou knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="8e839-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="8e839-111">Inicializuje ke spuštění spravované EXE.</span><span class="sxs-lookup"><span data-stu-id="8e839-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="8e839-112">To inicializuje modul runtime, ale nevytvoří výchozí <xref:System.AppDomain>, který je vytvořen po zadání rutinu EXE.</span><span class="sxs-lookup"><span data-stu-id="8e839-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8e839-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8e839-113">Requirements</span></span>  
 <span data-ttu-id="8e839-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e839-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e839-115">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8e839-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8e839-116">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8e839-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8e839-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e839-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e839-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e839-118">See Also</span></span>  
 [<span data-ttu-id="8e839-119">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="8e839-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
