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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15fd75ae807ee5cd7f94f6e650639c3be0628429
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136536"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="42493-102">IMetaDataEmit::DefinePinvokeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="42493-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="42493-103">Nastaví funkce PInvoke podpis metody odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="42493-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42493-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42493-104">Syntax</span></span>  
  
```  
HRESULT DefinePinvokeMap (   
    [in]  mdToken            tk,   
    [in]  DWORD              dwMappingFlags,   
    [in]  LPCWSTR            szImportName,   
    [in]  mdModuleRef        mrImportDLL   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42493-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42493-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="42493-106">[in] Token pro cílové metody.</span><span class="sxs-lookup"><span data-stu-id="42493-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="42493-107">[in] Příznaky používá u PInvoke k proveďte mapování.</span><span class="sxs-lookup"><span data-stu-id="42493-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="42493-108">[in] Název cíle metoda export ve nespravovaná knihovna DLL.</span><span class="sxs-lookup"><span data-stu-id="42493-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="42493-109">[in] Token pro cíl nativní knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="42493-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42493-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42493-110">Requirements</span></span>  
 <span data-ttu-id="42493-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42493-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42493-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="42493-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="42493-113">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="42493-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42493-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42493-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42493-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42493-115">See also</span></span>

- [<span data-ttu-id="42493-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42493-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="42493-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42493-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
