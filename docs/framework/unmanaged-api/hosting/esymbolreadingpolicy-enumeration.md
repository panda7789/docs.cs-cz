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
ms.openlocfilehash: 5c3d1d0ebc56ee93c950afb4f015c8e10ec6a0f7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616172"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="f0c10-102">ESymbolReadingPolicy – výčet</span><span class="sxs-lookup"><span data-stu-id="f0c10-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="f0c10-103">Obsahuje hodnoty, které nastavují zásady pro soubory programu pro čtení databáze programu (PDB).</span><span class="sxs-lookup"><span data-stu-id="f0c10-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0c10-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0c10-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="f0c10-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f0c10-105">Members</span></span>  
  
|<span data-ttu-id="f0c10-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f0c10-106">Member</span></span>|<span data-ttu-id="f0c10-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f0c10-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="f0c10-108">Určuje, že ladicí program by měl vždy číst soubory PDB.</span><span class="sxs-lookup"><span data-stu-id="f0c10-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="f0c10-109">Určuje, že ladicí program by měl číst pouze soubory PDB, které jsou přidruženy k sestavením s úplným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="f0c10-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="f0c10-110">Určuje, že ladicí program by neměl nikdy číst soubory PDB.</span><span class="sxs-lookup"><span data-stu-id="f0c10-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0c10-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f0c10-111">Remarks</span></span>  
 <span data-ttu-id="f0c10-112">`ESymbolReadingPolicy`Výčet se používá s metodou [ICLRDebugManager:: SetSymbolReadingPolicy –](iclrdebugmanager-setsymbolreadingpolicy-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f0c10-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0c10-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f0c10-113">Requirements</span></span>  
 <span data-ttu-id="f0c10-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0c10-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0c10-115">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f0c10-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0c10-116">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f0c10-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0c10-117">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0c10-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0c10-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0c10-118">See also</span></span>

- [<span data-ttu-id="f0c10-119">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="f0c10-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
