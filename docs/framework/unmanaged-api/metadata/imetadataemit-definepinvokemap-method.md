---
title: IMetaDataEmit::DefinePinvokeMap – metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: e414bc5a7d537e8d153541f05b22dd91578e8739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177742"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="42115-102">IMetaDataEmit::DefinePinvokeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="42115-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="42115-103">Nastaví funkce pinvoke podpisu metody odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="42115-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42115-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42115-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePinvokeMap (
    [in]  mdToken            tk,
    [in]  DWORD              dwMappingFlags,
    [in]  LPCWSTR            szImportName,
    [in]  mdModuleRef        mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42115-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42115-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="42115-106">[v] Token pro cílovou metodu.</span><span class="sxs-lookup"><span data-stu-id="42115-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="42115-107">[v] Příznaky používané PInvoke k mapování.</span><span class="sxs-lookup"><span data-stu-id="42115-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="42115-108">[v] Název cílové metody exportu v nespravované dll.</span><span class="sxs-lookup"><span data-stu-id="42115-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="42115-109">[v] Token pro cílovou nativní dll.</span><span class="sxs-lookup"><span data-stu-id="42115-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42115-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42115-110">Requirements</span></span>  
 <span data-ttu-id="42115-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42115-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42115-112">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="42115-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="42115-113">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="42115-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42115-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42115-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42115-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="42115-115">See also</span></span>

- [<span data-ttu-id="42115-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42115-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="42115-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42115-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
