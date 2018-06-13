---
title: ASM_DISPLAY_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- ASM_DISPLAY_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_DISPLAY_FLAGS
helpviewer_keywords:
- ASM_DISPLAY_FLAGS enumeration [.NET Framework fusion]
ms.assetid: dbade6c9-9d26-4a79-9fd2-46108edd12d7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9607aa99e1f1dbe0af3a868a32c70cd83d5e66a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429527"
---
# <a name="asmdisplayflags-enumeration"></a><span data-ttu-id="41e23-102">ASM_DISPLAY_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="41e23-102">ASM_DISPLAY_FLAGS Enumeration</span></span>
<span data-ttu-id="41e23-103">Určuje verzi, sestavení, jazykovou verzi, podpisu a tak dále, sestavení, jehož zobrazovaný název bude načten pomocí [iassemblyname::GetDisplayName –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="41e23-103">Indicates the version, build, culture, signature, and so on, of the assembly whose display name will be retrieved by the [IAssemblyName::GetDisplayName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41e23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41e23-104">Syntax</span></span>  
  
```  
typedef enum {  
  
    ASM_DISPLAYF_VERSION                 = 0x01,  
    ASM_DISPLAYF_CULTURE                 = 0x02,  
    ASM_DISPLAYF_PUBLIC_KEY_TOKEN        = 0x04,  
    ASM_DISPLAYF_PUBLIC_KEY              = 0x08,  
    ASM_DISPLAYF_CUSTOM                  = 0x10,  
    ASM_DISPLAYF_PROCESSORARCHITECTURE   = 0x20,  
    ASM_DISPLAYF_LANGUAGEID              = 0x40,  
    ASM_DISPLAYF_RETARGET                = 0x80,  
    ASM_DISPLAYF_CONFIG_MASK             = 0x100,  
    ASM_DISPLAYF_MVID                    = 0x200,  
    ASM_DISPLAYF_FULL                    =   
                      ASM_DISPLAYF_VERSION           |   
                      ASM_DISPLAYF_CULTURE           |   
                      ASM_DISPLAYF_PUBLIC_KEY_TOKEN  |   
                      ASM_DISPLAYF_RETARGET          |   
                      ASM_DISPLAYF_PROCESSORARCHITECTURE  
  
} ASM_DISPLAY_FLAGS;  
```  
  
## <a name="remarks"></a><span data-ttu-id="41e23-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="41e23-105">Remarks</span></span>  
 <span data-ttu-id="41e23-106">`ASM_DISPLAYF_FULL` odráží všechny změny na verzi [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="41e23-106">`ASM_DISPLAYF_FULL` reflects any changes made to the version of the [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span> <span data-ttu-id="41e23-107">Nepředpokládejte, že vrácená hodnota se nedá změnit.</span><span class="sxs-lookup"><span data-stu-id="41e23-107">Do not assume that the returned value is immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41e23-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="41e23-108">Requirements</span></span>  
 <span data-ttu-id="41e23-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41e23-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41e23-110">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="41e23-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="41e23-111">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="41e23-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="41e23-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41e23-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41e23-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="41e23-113">See Also</span></span>  
 [<span data-ttu-id="41e23-114">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="41e23-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="41e23-115">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="41e23-115">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
