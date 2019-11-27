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
ms.openlocfilehash: 2ccc038b4420040779dae70f15e3a8827ba94180
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444113"
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="a46a0-102">COINITIEE – výčet</span><span class="sxs-lookup"><span data-stu-id="a46a0-102">COINITIEE Enumeration</span></span>
<span data-ttu-id="a46a0-103">Určuje konstanty, které používá [CoInitializeEE –](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) při inicializaci modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="a46a0-103">Specifies constants used by [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a46a0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a46a0-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="a46a0-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a46a0-105">Members</span></span>  
  
|<span data-ttu-id="a46a0-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a46a0-106">Member</span></span>|<span data-ttu-id="a46a0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a46a0-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="a46a0-108">Výchozí režim inicializace.</span><span class="sxs-lookup"><span data-stu-id="a46a0-108">Default initialization mode.</span></span> <span data-ttu-id="a46a0-109">Tím se Inicializuje modul runtime a vytvoří se výchozí <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="a46a0-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="a46a0-110">Inicializuje spuštění spravované knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="a46a0-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="a46a0-111">Inicializuje pro spuštění spravovaného souboru EXE.</span><span class="sxs-lookup"><span data-stu-id="a46a0-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="a46a0-112">Tím se Inicializuje modul runtime, ale nevytvoří se výchozí <xref:System.AppDomain>, který se vytvoří po zadání hlavní rutiny EXE.</span><span class="sxs-lookup"><span data-stu-id="a46a0-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a46a0-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a46a0-113">Requirements</span></span>  
 <span data-ttu-id="a46a0-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a46a0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a46a0-115">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a46a0-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a46a0-116">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a46a0-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a46a0-117">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a46a0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a46a0-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a46a0-118">See also</span></span>

- [<span data-ttu-id="a46a0-119">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="a46a0-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
