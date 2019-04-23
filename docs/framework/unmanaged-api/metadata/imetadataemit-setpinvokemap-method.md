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
ms.openlocfilehash: b838a83a160707e546b05ef334eb17d0c6e6cc27
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133559"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="abe3c-102">IMetaDataEmit::SetPinvokeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="abe3c-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="abe3c-103">Nastavuje nebo mění určené předchozím volání funkce PInvoke signatury metody, [imetadataemit::definepinvokemap –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span><span class="sxs-lookup"><span data-stu-id="abe3c-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abe3c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abe3c-104">Syntax</span></span>  
  
```  
HRESULT SetPinvokeMap (   
    [in]  mdToken      tk,   
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,   
    [in]  mdModuleRef  mrImportDLL   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abe3c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="abe3c-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="abe3c-106">[in] `mdToken` Mapování, které informace se vztahují.</span><span class="sxs-lookup"><span data-stu-id="abe3c-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="abe3c-107">[in] Příznaky používá u PInvoke k proveďte mapování.</span><span class="sxs-lookup"><span data-stu-id="abe3c-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="abe3c-108">To je bitová maska z `CorPinvokeMap` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="abe3c-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="abe3c-109">[in] Název cíle export v nativní knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="abe3c-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="abe3c-110">[in] `mdModuleRef` Token pro cíl nespravovaná knihovna DLL.</span><span class="sxs-lookup"><span data-stu-id="abe3c-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abe3c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="abe3c-111">Requirements</span></span>  
 <span data-ttu-id="abe3c-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abe3c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abe3c-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="abe3c-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="abe3c-114">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="abe3c-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="abe3c-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abe3c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abe3c-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="abe3c-116">See also</span></span>

- [<span data-ttu-id="abe3c-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="abe3c-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="abe3c-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="abe3c-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
