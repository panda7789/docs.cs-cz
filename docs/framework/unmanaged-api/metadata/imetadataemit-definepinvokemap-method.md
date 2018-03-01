---
title: "IMetaDataEmit::DefinePinvokeMap – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit.DefinePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePinvokeMap
helpviewer_keywords:
- DefinePinvokeMap method [.NET Framework metadata]
- IMetaDataEmit::DefinePinvokeMap method [.NET Framework metadata]
ms.assetid: 03abf921-5154-4070-88fa-10b7092901fb
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bd42c54990fd8aad1b9e6325d59ac7ccc5d6a3fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="d7604-102">IMetaDataEmit::DefinePinvokeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="d7604-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="d7604-103">Nastaví funkce PInvoke podpis metody odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="d7604-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7604-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7604-104">Syntax</span></span>  
  
```  
HRESULT DefinePinvokeMap (   
    [in]  mdToken            tk,   
    [in]  DWORD              dwMappingFlags,   
    [in]  LPCWSTR            szImportName,   
    [in]  mdModuleRef        mrImportDLL   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7604-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7604-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="d7604-106">[v] Token pro cílové metody.</span><span class="sxs-lookup"><span data-stu-id="d7604-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="d7604-107">[v] Příznaky použité PInvoke udělat mapování.</span><span class="sxs-lookup"><span data-stu-id="d7604-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="d7604-108">[v] Název cílového exportovat metoda v nespravované knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="d7604-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="d7604-109">[v] Token pro cíl nativní knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="d7604-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7604-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7604-110">Requirements</span></span>  
 <span data-ttu-id="d7604-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7604-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7604-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d7604-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d7604-113">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d7604-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7604-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7604-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7604-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7604-115">See Also</span></span>  
 [<span data-ttu-id="d7604-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7604-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="d7604-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7604-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
