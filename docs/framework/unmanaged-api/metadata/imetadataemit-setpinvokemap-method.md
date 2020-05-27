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
ms.openlocfilehash: 0d34c7a2992a2779b96ec87f1a0175d8fcbce34a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007790"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="9f296-102">IMetaDataEmit::SetPinvokeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="9f296-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="9f296-103">Nastaví nebo změní funkce signatury PInvoke metody, jak je definováno předchozím voláním [IMetaDataEmit::D efinepinvokemap](imetadataemit-definepinvokemap-method.md).</span><span class="sxs-lookup"><span data-stu-id="9f296-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f296-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f296-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPinvokeMap (
    [in]  mdToken      tk,
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,
    [in]  mdModuleRef  mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f296-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f296-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="9f296-106">pro , `mdToken` Na které se vztahují informace o mapování.</span><span class="sxs-lookup"><span data-stu-id="9f296-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="9f296-107">pro Příznaky používané v PInvoke k mapování.</span><span class="sxs-lookup"><span data-stu-id="9f296-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="9f296-108">Toto je Bitová maska `CorPinvokeMap` hodnot.</span><span class="sxs-lookup"><span data-stu-id="9f296-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="9f296-109">pro Název cílového exportu v nativní knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="9f296-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="9f296-110">pro `mdModuleRef`Token pro cílovou nespravovanou knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="9f296-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f296-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f296-111">Requirements</span></span>  
 <span data-ttu-id="9f296-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f296-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f296-113">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9f296-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9f296-114">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="9f296-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9f296-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f296-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f296-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f296-116">See also</span></span>

- [<span data-ttu-id="9f296-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9f296-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="9f296-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9f296-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
