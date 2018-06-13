---
title: IMetaDataEmit::SetPinvokeMap – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84b2c0571a7991829e65b45759bd61fa4009aa71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445874"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="e4635-102">IMetaDataEmit::SetPinvokeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="e4635-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="e4635-103">Nastaví nebo změny funkcí metoda PInvoke podpis, podle definice předchozí volání [imetadataemit::definepinvokemap –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span><span class="sxs-lookup"><span data-stu-id="e4635-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4635-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4635-104">Syntax</span></span>  
  
```  
HRESULT SetPinvokeMap (   
    [in]  mdToken      tk,   
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,   
    [in]  mdModuleRef  mrImportDLL   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4635-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4635-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="e4635-106">[v] `mdToken` Pro mapování, které informace se vztahují.</span><span class="sxs-lookup"><span data-stu-id="e4635-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="e4635-107">[v] Příznaky použité PInvoke udělat mapování.</span><span class="sxs-lookup"><span data-stu-id="e4635-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="e4635-108">Toto je bitová maska s `CorPinvokeMap` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e4635-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="e4635-109">[v] Název cílového exportovat v nativní knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="e4635-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="e4635-110">[v] `mdModuleRef` Tokenu pro cíl nespravované knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="e4635-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4635-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e4635-111">Requirements</span></span>  
 <span data-ttu-id="e4635-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4635-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4635-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e4635-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e4635-114">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e4635-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4635-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4635-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4635-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4635-116">See Also</span></span>  
 [<span data-ttu-id="e4635-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4635-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="e4635-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4635-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
