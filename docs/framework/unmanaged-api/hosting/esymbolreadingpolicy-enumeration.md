---
title: "ESymbolReadingPolicy – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ESymbolReadingPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ESymbolReadingPolicy
helpviewer_keywords: ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ce56486453e88a18ebd9dbb42f30bcfdafcf328e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="6fb3b-102">ESymbolReadingPolicy – výčet</span><span class="sxs-lookup"><span data-stu-id="6fb3b-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="6fb3b-103">Obsahuje hodnoty, které nastavit zásady pro soubory databáze (PDB) program pro čtení.</span><span class="sxs-lookup"><span data-stu-id="6fb3b-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fb3b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fb3b-104">Syntax</span></span>  
  
```  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="6fb3b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="6fb3b-105">Members</span></span>  
  
|<span data-ttu-id="6fb3b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="6fb3b-106">Member</span></span>|<span data-ttu-id="6fb3b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6fb3b-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="6fb3b-108">Určuje, že ladicí program vždy číst soubory PDB.</span><span class="sxs-lookup"><span data-stu-id="6fb3b-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="6fb3b-109">Určuje, že ladicí program by měl číst pouze soubory PDB, které jsou přidruženy sestavení plné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="6fb3b-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="6fb3b-110">Určuje, že ladicího programu nikdy číst soubory PDB.</span><span class="sxs-lookup"><span data-stu-id="6fb3b-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fb3b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6fb3b-111">Remarks</span></span>  
 <span data-ttu-id="6fb3b-112">`ESymbolReadingPolicy` Výčtu se používá s [iclrdebugmanager::setsymbolreadingpolicy –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="6fb3b-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fb3b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6fb3b-113">Requirements</span></span>  
 <span data-ttu-id="6fb3b-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fb3b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fb3b-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6fb3b-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6fb3b-116">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6fb3b-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6fb3b-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fb3b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fb3b-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="6fb3b-118">See Also</span></span>  
 [<span data-ttu-id="6fb3b-119">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="6fb3b-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
