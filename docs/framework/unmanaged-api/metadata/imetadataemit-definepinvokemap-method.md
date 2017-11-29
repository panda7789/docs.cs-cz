---
title: "IMetaDataEmit::DefinePinvokeMap – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefinePinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefinePinvokeMap
helpviewer_keywords:
- DefinePinvokeMap method [.NET Framework metadata]
- IMetaDataEmit::DefinePinvokeMap method [.NET Framework metadata]
ms.assetid: 03abf921-5154-4070-88fa-10b7092901fb
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0c15c6039f116597ee4f2c0f83bed4c5550b30a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="cf216-102">IMetaDataEmit::DefinePinvokeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="cf216-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="cf216-103">Nastaví funkce PInvoke podpis metody odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="cf216-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf216-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf216-104">Syntax</span></span>  
  
```  
HRESULT DefinePinvokeMap (   
    [in]  mdToken            tk,   
    [in]  DWORD              dwMappingFlags,   
    [in]  LPCWSTR            szImportName,   
    [in]  mdModuleRef        mrImportDLL   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf216-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cf216-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="cf216-106">[v] Token pro cílové metody.</span><span class="sxs-lookup"><span data-stu-id="cf216-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="cf216-107">[v] Příznaky použité PInvoke udělat mapování.</span><span class="sxs-lookup"><span data-stu-id="cf216-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="cf216-108">[v] Název cílového exportovat metoda v nespravované knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="cf216-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="cf216-109">[v] Token pro cíl nativní knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="cf216-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf216-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cf216-110">Requirements</span></span>  
 <span data-ttu-id="cf216-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf216-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf216-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cf216-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cf216-113">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf216-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf216-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf216-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf216-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf216-115">See Also</span></span>  
 [<span data-ttu-id="cf216-116">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf216-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="cf216-117">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf216-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
