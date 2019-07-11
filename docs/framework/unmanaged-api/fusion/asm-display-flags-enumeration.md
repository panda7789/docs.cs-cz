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
ms.openlocfilehash: 70b40095ffcfea37414b7de2a678ad8555423b12
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778554"
---
# <a name="asmdisplayflags-enumeration"></a><span data-ttu-id="2eb1f-102">ASM_DISPLAY_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="2eb1f-102">ASM_DISPLAY_FLAGS Enumeration</span></span>
<span data-ttu-id="2eb1f-103">Určuje verzi, sestavení, jazykovou verzi, podpisu a tak dále, sestavení, jejichž zobrazované jméno bude možné načíst podle [iassemblyname::GetDisplayName –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2eb1f-103">Indicates the version, build, culture, signature, and so on, of the assembly whose display name will be retrieved by the [IAssemblyName::GetDisplayName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2eb1f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2eb1f-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="remarks"></a><span data-ttu-id="2eb1f-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2eb1f-105">Remarks</span></span>  
 <span data-ttu-id="2eb1f-106">`ASM_DISPLAYF_FULL` odráží všechny změny provedené na verzi [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="2eb1f-106">`ASM_DISPLAYF_FULL` reflects any changes made to the version of the [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span> <span data-ttu-id="2eb1f-107">Nepředpokládejte, že vrácená hodnota je neměnná.</span><span class="sxs-lookup"><span data-stu-id="2eb1f-107">Do not assume that the returned value is immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2eb1f-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2eb1f-108">Requirements</span></span>  
 <span data-ttu-id="2eb1f-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2eb1f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2eb1f-110">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="2eb1f-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="2eb1f-111">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2eb1f-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2eb1f-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2eb1f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eb1f-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2eb1f-113">See also</span></span>

- [<span data-ttu-id="2eb1f-114">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2eb1f-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="2eb1f-115">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="2eb1f-115">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
