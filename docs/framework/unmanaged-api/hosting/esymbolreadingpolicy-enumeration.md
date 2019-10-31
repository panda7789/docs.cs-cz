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
ms.openlocfilehash: 786ff6895383fc18dcfedb26fab344f80f04c1df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138209"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="fe3c7-102">ESymbolReadingPolicy – výčet</span><span class="sxs-lookup"><span data-stu-id="fe3c7-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="fe3c7-103">Obsahuje hodnoty, které nastavují zásady pro soubory programu pro čtení databáze programu (PDB).</span><span class="sxs-lookup"><span data-stu-id="fe3c7-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe3c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe3c7-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="fe3c7-105">Členové</span><span class="sxs-lookup"><span data-stu-id="fe3c7-105">Members</span></span>  
  
|<span data-ttu-id="fe3c7-106">Člen</span><span class="sxs-lookup"><span data-stu-id="fe3c7-106">Member</span></span>|<span data-ttu-id="fe3c7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="fe3c7-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="fe3c7-108">Určuje, že ladicí program by měl vždy číst soubory PDB.</span><span class="sxs-lookup"><span data-stu-id="fe3c7-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="fe3c7-109">Určuje, že ladicí program by měl číst pouze soubory PDB, které jsou přidruženy k sestavením s úplným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="fe3c7-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="fe3c7-110">Určuje, že ladicí program by neměl nikdy číst soubory PDB.</span><span class="sxs-lookup"><span data-stu-id="fe3c7-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe3c7-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe3c7-111">Remarks</span></span>  
 <span data-ttu-id="fe3c7-112">`ESymbolReadingPolicy` výčet se používá s metodou [ICLRDebugManager:: SetSymbolReadingPolicy –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fe3c7-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe3c7-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe3c7-113">Requirements</span></span>  
 <span data-ttu-id="fe3c7-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe3c7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe3c7-115">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fe3c7-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fe3c7-116">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fe3c7-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe3c7-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe3c7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe3c7-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe3c7-118">See also</span></span>

- [<span data-ttu-id="fe3c7-119">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="fe3c7-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
