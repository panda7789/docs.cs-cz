---
title: EHostBindingPolicyModifyFlags – výčet
ms.date: 03/30/2017
api_name:
- EHostBindingPolicyModifyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EHostBindingPolicyModifyFlags
helpviewer_keywords:
- EHostBindingPolicyModifyFlags enumeration [.NET Framework hosting]
ms.assetid: 0339af16-ee1d-48ec-837d-a79d9a9c89f8
topic_type:
- apiref
ms.openlocfilehash: a2faf22b48dd0b809d6c3668a37f2119733a9b18
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129439"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="20a6f-102">EHostBindingPolicyModifyFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="20a6f-102">EHostBindingPolicyModifyFlags Enumeration</span></span>
<span data-ttu-id="20a6f-103">Umožňuje hostiteli určit typ přesměrování, který modul CLR (Common Language Runtime) by měl provést při použití změn zásad ze zdrojového sestavení na cílové sestavení.</span><span class="sxs-lookup"><span data-stu-id="20a6f-103">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20a6f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20a6f-104">Syntax</span></span>  
  
```cpp  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="20a6f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="20a6f-105">Members</span></span>  
  
|<span data-ttu-id="20a6f-106">Člen</span><span class="sxs-lookup"><span data-stu-id="20a6f-106">Member</span></span>|<span data-ttu-id="20a6f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="20a6f-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="20a6f-108">Určuje, že CLR bude řetězit hodnoty zásad zdrojového sestavení do cílových sestavení.</span><span class="sxs-lookup"><span data-stu-id="20a6f-108">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="20a6f-109">Určuje, že modul CLR provede výchozí akci.</span><span class="sxs-lookup"><span data-stu-id="20a6f-109">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="20a6f-110">Určuje, že CLR nastaví hodnoty zásad cílového sestavení na maximální hodnoty.</span><span class="sxs-lookup"><span data-stu-id="20a6f-110">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="20a6f-111">Určuje, že CLR nahradí hodnoty zásad cílového sestavení prvky zdrojového sestavení.</span><span class="sxs-lookup"><span data-stu-id="20a6f-111">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20a6f-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20a6f-112">Remarks</span></span>  
 <span data-ttu-id="20a6f-113">Metoda [ICLRHostBindingPolicyManager:: ModifyApplicationPolicy –](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) přebírá parametr typu `EHostBindingPolicyModifyFlags`.</span><span class="sxs-lookup"><span data-stu-id="20a6f-113">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20a6f-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20a6f-114">Requirements</span></span>  
 <span data-ttu-id="20a6f-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20a6f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20a6f-116">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="20a6f-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20a6f-117">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="20a6f-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20a6f-118">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20a6f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20a6f-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20a6f-119">See also</span></span>

- [<span data-ttu-id="20a6f-120">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20a6f-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="20a6f-121">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="20a6f-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
