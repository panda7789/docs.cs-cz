---
title: "IMetaDataEmit::SetPinvokeMap – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetPinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a10482b12f9a34b0f247779f22c7cc70f871324a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="1b880-102">IMetaDataEmit::SetPinvokeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="1b880-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="1b880-103">Nastaví nebo změny funkcí metoda PInvoke podpis, podle definice předchozí volání [imetadataemit::definepinvokemap –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span><span class="sxs-lookup"><span data-stu-id="1b880-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b880-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b880-104">Syntax</span></span>  
  
```  
HRESULT SetPinvokeMap (   
    [in]  mdToken      tk,   
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,   
    [in]  mdModuleRef  mrImportDLL   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b880-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1b880-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="1b880-106">[v] `mdToken` Pro mapování, které informace se vztahují.</span><span class="sxs-lookup"><span data-stu-id="1b880-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="1b880-107">[v] Příznaky použité PInvoke udělat mapování.</span><span class="sxs-lookup"><span data-stu-id="1b880-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="1b880-108">Toto je bitová maska s `CorPinvokeMap` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1b880-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="1b880-109">[v] Název cílového exportovat v nativní knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="1b880-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="1b880-110">[v] `mdModuleRef` Tokenu pro cíl nespravované knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="1b880-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b880-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1b880-111">Requirements</span></span>  
 <span data-ttu-id="1b880-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b880-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b880-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1b880-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1b880-114">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1b880-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b880-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b880-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b880-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b880-116">See Also</span></span>  
 [<span data-ttu-id="1b880-117">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b880-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="1b880-118">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b880-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
