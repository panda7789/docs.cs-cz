---
title: "ASM_NAME – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASM_NAME
api_location: fusion.dll
api_type: COM
f1_keywords: ASM_NAME
helpviewer_keywords: ASM_NAME enumeration [.NET Framework fusion]
ms.assetid: c8b65b19-d777-428f-bc0c-0d84c78a37bc
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fb247f85984cff167e9e0ce729a5143633a3f7c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="asmname-enumeration"></a><span data-ttu-id="82ecd-102">ASM_NAME – výčet</span><span class="sxs-lookup"><span data-stu-id="82ecd-102">ASM_NAME Enumeration</span></span>
<span data-ttu-id="82ecd-103">Určuje verzi, sestavení, jazykovou verzi, podpisu a tak dále, sestavení, jehož vlastnosti se načíst nebo nastavit [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) metody.</span><span class="sxs-lookup"><span data-stu-id="82ecd-103">Indicates the version, build, culture, signature, and so on, of the assembly whose properties will be retrieved or set by [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82ecd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82ecd-104">Syntax</span></span>  
  
```  
typedef enum {  
  
    ASM_NAME_PUBLIC_KEY = 0,  
    ASM_NAME_PUBLIC_KEY_TOKEN,  
    ASM_NAME_HASH_VALUE,  
    ASM_NAME_NAME,  
    ASM_NAME_MAJOR_VERSION,  
    ASM_NAME_MINOR_VERSION,  
    ASM_NAME_BUILD_NUMBER,  
    ASM_NAME_REVISION_NUMBER,  
    ASM_NAME_CULTURE,  
    ASM_NAME_PROCESSOR_ID_ARRAY,  
    ASM_NAME_OSINFO_ARRAY,  
    ASM_NAME_HASH_ALGID,  
    ASM_NAME_ALIAS,  
    ASM_NAME_CODEBASE_URL,  
    ASM_NAME_CODEBASE_LASTMOD,  
    ASM_NAME_NULL_PUBLIC_KEY,  
    ASM_NAME_NULL_PUBLIC_KEY_TOKEN,  
    ASM_NAME_CUSTOM,  
    ASM_NAME_NULL_CUSTOM,   
    ASM_NAME_MVID,  
    ASM_NAME_FILE_MAJOR_VERSION,  
    ASM_NAME_FILE_MINOR_VERSION,  
    ASM_NAME_FILE_BUILD_NUMBER,  
    ASM_NAME_FILE_REVISION_NUMBER,  
    ASM_NAME_RETARGET,  
    ASM_NAME_SIGNATURE_BLOB,  
    ASM_NAME_CONFIG_MASK,  
    ASM_NAME_ARCHITECTURE,  
    ASM_NAME_MAX_PARAMS  
  
} ASM_NAME;  
```  
  
## <a name="requirements"></a><span data-ttu-id="82ecd-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82ecd-105">Requirements</span></span>  
 <span data-ttu-id="82ecd-106">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82ecd-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82ecd-107">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="82ecd-107">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="82ecd-108">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="82ecd-108">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="82ecd-109">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82ecd-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82ecd-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="82ecd-110">See Also</span></span>  
 [<span data-ttu-id="82ecd-111">Iassemblyname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82ecd-111">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="82ecd-112">Výčty fúzí</span><span class="sxs-lookup"><span data-stu-id="82ecd-112">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
