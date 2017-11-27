---
title: "ASM_DISPLAY_FLAGS – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASM_DISPLAY_FLAGS
api_location: fusion.dll
api_type: COM
f1_keywords: ASM_DISPLAY_FLAGS
helpviewer_keywords: ASM_DISPLAY_FLAGS enumeration [.NET Framework fusion]
ms.assetid: dbade6c9-9d26-4a79-9fd2-46108edd12d7
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5e9fcd6cc8c1a352567f635e848d49e322a35ea6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="asmdisplayflags-enumeration"></a><span data-ttu-id="fc126-102">ASM_DISPLAY_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="fc126-102">ASM_DISPLAY_FLAGS Enumeration</span></span>
<span data-ttu-id="fc126-103">Určuje verzi, sestavení, jazykovou verzi, podpisu a tak dále, sestavení, jehož zobrazovaný název bude načten pomocí [iassemblyname::GetDisplayName –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="fc126-103">Indicates the version, build, culture, signature, and so on, of the assembly whose display name will be retrieved by the [IAssemblyName::GetDisplayName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc126-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc126-104">Syntax</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="fc126-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc126-105">Remarks</span></span>  
 <span data-ttu-id="fc126-106">`ASM_DISPLAYF_FULL`odráží všechny změny na verzi [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="fc126-106">`ASM_DISPLAYF_FULL` reflects any changes made to the version of the [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span> <span data-ttu-id="fc126-107">Nepředpokládejte, že vrácená hodnota se nedá změnit.</span><span class="sxs-lookup"><span data-stu-id="fc126-107">Do not assume that the returned value is immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc126-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc126-108">Requirements</span></span>  
 <span data-ttu-id="fc126-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc126-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc126-110">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="fc126-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="fc126-111">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fc126-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fc126-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc126-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc126-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc126-113">See Also</span></span>  
 [<span data-ttu-id="fc126-114">Iassemblyname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fc126-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="fc126-115">Výčty fúzí</span><span class="sxs-lookup"><span data-stu-id="fc126-115">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
