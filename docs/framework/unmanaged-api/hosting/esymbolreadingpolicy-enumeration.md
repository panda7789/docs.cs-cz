---
title: ESymbolReadingPolicy – výčet
ms.date: 03/30/2017
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ba29952fe4a6edfc6e9e80ec02f82de65ef0064
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61628597"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="e4b63-102">ESymbolReadingPolicy – výčet</span><span class="sxs-lookup"><span data-stu-id="e4b63-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="e4b63-103">Obsahuje hodnoty, které nastavení zásad pro čtení souborů databáze (PDB) programu.</span><span class="sxs-lookup"><span data-stu-id="e4b63-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4b63-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4b63-104">Syntax</span></span>  
  
```  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="e4b63-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e4b63-105">Members</span></span>  
  
|<span data-ttu-id="e4b63-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e4b63-106">Member</span></span>|<span data-ttu-id="e4b63-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e4b63-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="e4b63-108">Určuje, že ladicí program by měl vždy číst soubory PDB.</span><span class="sxs-lookup"><span data-stu-id="e4b63-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="e4b63-109">Určuje, že by měl ladicí program číst pouze soubory PDB, které jsou spojeny s plnou důvěryhodností sestavení.</span><span class="sxs-lookup"><span data-stu-id="e4b63-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="e4b63-110">Určuje, že ladicí program nikdy číst soubory PDB.</span><span class="sxs-lookup"><span data-stu-id="e4b63-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4b63-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e4b63-111">Remarks</span></span>  
 <span data-ttu-id="e4b63-112">`ESymbolReadingPolicy` Výčtu se používá s [iclrdebugmanager::setsymbolreadingpolicy –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e4b63-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4b63-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e4b63-113">Requirements</span></span>  
 <span data-ttu-id="e4b63-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4b63-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4b63-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e4b63-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4b63-116">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e4b63-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4b63-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4b63-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4b63-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4b63-118">See also</span></span>

- [<span data-ttu-id="e4b63-119">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="e4b63-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
