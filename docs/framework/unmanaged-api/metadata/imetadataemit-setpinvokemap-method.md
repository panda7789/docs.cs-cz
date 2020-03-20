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
ms.openlocfilehash: 4c68754bc44fe035fd8e7143c52895928beae395
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175587"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="0f8fd-102">IMetaDataEmit::SetPinvokeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="0f8fd-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="0f8fd-103">Nastaví nebo změní funkce pinvoke podpisu metody, jak je definováno předchozí volání [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span><span class="sxs-lookup"><span data-stu-id="0f8fd-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f8fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f8fd-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPinvokeMap (
    [in]  mdToken      tk,
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,
    [in]  mdModuleRef  mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f8fd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0f8fd-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="0f8fd-106">[v] Na `mdToken` které se vztahují informace o mapování.</span><span class="sxs-lookup"><span data-stu-id="0f8fd-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="0f8fd-107">[v] Příznaky používané PInvoke k mapování.</span><span class="sxs-lookup"><span data-stu-id="0f8fd-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="0f8fd-108">Toto je bitová maska `CorPinvokeMap` hodnot.</span><span class="sxs-lookup"><span data-stu-id="0f8fd-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="0f8fd-109">[v] Název cílového exportu v nativní dll.</span><span class="sxs-lookup"><span data-stu-id="0f8fd-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="0f8fd-110">[v] Token `mdModuleRef` pro cílovou nespravovanou dll.</span><span class="sxs-lookup"><span data-stu-id="0f8fd-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f8fd-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0f8fd-111">Requirements</span></span>  
 <span data-ttu-id="0f8fd-112">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f8fd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f8fd-113">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="0f8fd-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0f8fd-114">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0f8fd-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f8fd-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f8fd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f8fd-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f8fd-116">See also</span></span>

- [<span data-ttu-id="0f8fd-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0f8fd-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="0f8fd-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0f8fd-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
