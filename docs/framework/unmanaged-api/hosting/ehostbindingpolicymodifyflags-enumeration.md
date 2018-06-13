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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fa8cc15f77ff59e3d3c570341d9bba70cf1e953
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431711"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="bb745-102">EHostBindingPolicyModifyFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="bb745-102">EHostBindingPolicyModifyFlags Enumeration</span></span>
<span data-ttu-id="bb745-103">Umožňuje hostiteli určovat typ přesměrování, které modul CLR (CLR) má provést při použití změny zásad ze sestavení zdrojové do cílové sestavení.</span><span class="sxs-lookup"><span data-stu-id="bb745-103">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb745-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb745-104">Syntax</span></span>  
  
```  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="bb745-105">Členové</span><span class="sxs-lookup"><span data-stu-id="bb745-105">Members</span></span>  
  
|<span data-ttu-id="bb745-106">Člen</span><span class="sxs-lookup"><span data-stu-id="bb745-106">Member</span></span>|<span data-ttu-id="bb745-107">Popis</span><span class="sxs-lookup"><span data-stu-id="bb745-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="bb745-108">Určuje, že modul CLR bude zřetězené hodnoty zásad zdroje sestavení do těch, které cíl sestavení.</span><span class="sxs-lookup"><span data-stu-id="bb745-108">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="bb745-109">Určuje, že modulu CLR provede výchozí akci.</span><span class="sxs-lookup"><span data-stu-id="bb745-109">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="bb745-110">Určuje, že modul CLR bude nastavit hodnoty zásad cíl sestavení na maximální hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bb745-110">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="bb745-111">Určuje, že modulu CLR nahradí hodnoty zásad cíl sestavení s těmi, která sestavení zdroje.</span><span class="sxs-lookup"><span data-stu-id="bb745-111">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb745-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bb745-112">Remarks</span></span>  
 <span data-ttu-id="bb745-113">[Iclrhostbindingpolicymanager::modifyapplicationpolicy –](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) metoda přebírá parametr typu `EHostBindingPolicyModifyFlags`.</span><span class="sxs-lookup"><span data-stu-id="bb745-113">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb745-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb745-114">Requirements</span></span>  
 <span data-ttu-id="bb745-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb745-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb745-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bb745-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb745-117">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bb745-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb745-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb745-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb745-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb745-119">See Also</span></span>  
 [<span data-ttu-id="bb745-120">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb745-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 [<span data-ttu-id="bb745-121">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="bb745-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
