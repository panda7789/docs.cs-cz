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
ms.openlocfilehash: 480fedc8ae63ffa3222a74e39297cc64b6812e97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444488"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="9f516-102">IMetaDataEmit::DefinePinvokeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="9f516-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="9f516-103">Nastaví funkce PInvoke podpis metody odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="9f516-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f516-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f516-104">Syntax</span></span>  
  
```  
HRESULT DefinePinvokeMap (   
    [in]  mdToken            tk,   
    [in]  DWORD              dwMappingFlags,   
    [in]  LPCWSTR            szImportName,   
    [in]  mdModuleRef        mrImportDLL   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9f516-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f516-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="9f516-106">[v] Token pro cílové metody.</span><span class="sxs-lookup"><span data-stu-id="9f516-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="9f516-107">[v] Příznaky použité PInvoke udělat mapování.</span><span class="sxs-lookup"><span data-stu-id="9f516-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="9f516-108">[v] Název cílového exportovat metoda v nespravované knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="9f516-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="9f516-109">[v] Token pro cíl nativní knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="9f516-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f516-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f516-110">Requirements</span></span>  
 <span data-ttu-id="9f516-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f516-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f516-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9f516-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9f516-113">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9f516-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9f516-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f516-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f516-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f516-115">See Also</span></span>  
 [<span data-ttu-id="9f516-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9f516-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="9f516-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9f516-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
