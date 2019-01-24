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
ms.openlocfilehash: 5f1d62c55df410d284fe050b805cf465718ab112
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576148"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="98617-102">IMetaDataEmit::DefinePinvokeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="98617-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="98617-103">Nastaví funkce PInvoke podpis metody odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="98617-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98617-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98617-104">Syntax</span></span>  
  
```  
HRESULT DefinePinvokeMap (   
    [in]  mdToken            tk,   
    [in]  DWORD              dwMappingFlags,   
    [in]  LPCWSTR            szImportName,   
    [in]  mdModuleRef        mrImportDLL   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="98617-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="98617-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="98617-106">[in] Token pro cílové metody.</span><span class="sxs-lookup"><span data-stu-id="98617-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="98617-107">[in] Příznaky používá u PInvoke k proveďte mapování.</span><span class="sxs-lookup"><span data-stu-id="98617-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="98617-108">[in] Název cíle metoda export ve nespravovaná knihovna DLL.</span><span class="sxs-lookup"><span data-stu-id="98617-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="98617-109">[in] Token pro cíl nativní knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="98617-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98617-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="98617-110">Requirements</span></span>  
 <span data-ttu-id="98617-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98617-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98617-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="98617-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="98617-113">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="98617-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98617-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98617-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98617-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98617-115">See also</span></span>
- [<span data-ttu-id="98617-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="98617-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="98617-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="98617-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
