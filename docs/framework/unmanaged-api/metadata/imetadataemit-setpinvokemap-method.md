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
ms.openlocfilehash: 4e2a78e2d049e952aa1be0b3a8fd640eb18d0320
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440565"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="bc1c1-102">IMetaDataEmit::SetPinvokeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="bc1c1-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="bc1c1-103">Nastaví nebo změní funkce signatury PInvoke metody, jak je definováno předchozím voláním [IMetaDataEmit::D efinepinvokemap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span><span class="sxs-lookup"><span data-stu-id="bc1c1-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc1c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc1c1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPinvokeMap (   
    [in]  mdToken      tk,   
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,   
    [in]  mdModuleRef  mrImportDLL   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc1c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc1c1-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="bc1c1-106">pro `mdToken`, na které se vztahují informace o mapování</span><span class="sxs-lookup"><span data-stu-id="bc1c1-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="bc1c1-107">pro Příznaky používané v PInvoke k mapování.</span><span class="sxs-lookup"><span data-stu-id="bc1c1-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="bc1c1-108">Toto je Bitová maska `CorPinvokeMap` hodnot.</span><span class="sxs-lookup"><span data-stu-id="bc1c1-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="bc1c1-109">pro Název cílového exportu v nativní knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="bc1c1-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="bc1c1-110">pro Token `mdModuleRef` pro cílovou nespravovanou knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="bc1c1-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc1c1-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bc1c1-111">Requirements</span></span>  
 <span data-ttu-id="bc1c1-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc1c1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc1c1-113">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bc1c1-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bc1c1-114">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="bc1c1-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc1c1-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc1c1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc1c1-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc1c1-116">See also</span></span>

- [<span data-ttu-id="bc1c1-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bc1c1-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="bc1c1-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bc1c1-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
