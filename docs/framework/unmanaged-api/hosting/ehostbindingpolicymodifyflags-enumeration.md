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
ms.openlocfilehash: 256c362ae0aea51fea16ce799db243b105dee81a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616239"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="00390-102">EHostBindingPolicyModifyFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="00390-102">EHostBindingPolicyModifyFlags Enumeration</span></span>
<span data-ttu-id="00390-103">Umožňuje hostiteli určit typ přesměrování, který modul CLR (Common Language Runtime) by měl provést při použití změn zásad ze zdrojového sestavení na cílové sestavení.</span><span class="sxs-lookup"><span data-stu-id="00390-103">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00390-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00390-104">Syntax</span></span>  
  
```cpp  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="00390-105">Členové</span><span class="sxs-lookup"><span data-stu-id="00390-105">Members</span></span>  
  
|<span data-ttu-id="00390-106">Člen</span><span class="sxs-lookup"><span data-stu-id="00390-106">Member</span></span>|<span data-ttu-id="00390-107">Popis</span><span class="sxs-lookup"><span data-stu-id="00390-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="00390-108">Určuje, že CLR bude řetězit hodnoty zásad zdrojového sestavení do cílových sestavení.</span><span class="sxs-lookup"><span data-stu-id="00390-108">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="00390-109">Určuje, že modul CLR provede výchozí akci.</span><span class="sxs-lookup"><span data-stu-id="00390-109">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="00390-110">Určuje, že CLR nastaví hodnoty zásad cílového sestavení na maximální hodnoty.</span><span class="sxs-lookup"><span data-stu-id="00390-110">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="00390-111">Určuje, že CLR nahradí hodnoty zásad cílového sestavení prvky zdrojového sestavení.</span><span class="sxs-lookup"><span data-stu-id="00390-111">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00390-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00390-112">Remarks</span></span>  
 <span data-ttu-id="00390-113">Metoda [ICLRHostBindingPolicyManager:: ModifyApplicationPolicy –](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) přebírá parametr typu `EHostBindingPolicyModifyFlags` .</span><span class="sxs-lookup"><span data-stu-id="00390-113">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00390-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00390-114">Requirements</span></span>  
 <span data-ttu-id="00390-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00390-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00390-116">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="00390-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="00390-117">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="00390-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00390-118">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00390-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00390-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="00390-119">See also</span></span>

- [<span data-ttu-id="00390-120">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00390-120">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="00390-121">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="00390-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
