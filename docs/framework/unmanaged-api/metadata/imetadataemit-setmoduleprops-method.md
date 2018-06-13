---
title: IMetaDataEmit::SetModuleProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetModuleProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetModuleProps
helpviewer_keywords:
- SetModuleProps method [.NET Framework metadata]
- IMetaDataEmit::SetModuleProps method [.NET Framework metadata]
ms.assetid: b74d7629-5f46-458f-8d67-2456a1e7030c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce8be38f6e146b2a8669ea5c694353615f6f2d66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445900"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="2a827-102">IMetaDataEmit::SetModuleProps – metoda</span><span class="sxs-lookup"><span data-stu-id="2a827-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="2a827-103">Aktualizace odkazů na modul definované předchozí volání [imetadataemit::definemoduleref –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="2a827-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a827-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a827-104">Syntax</span></span>  
  
```  
HRESULT SetModuleProps (   
    [in]  LPCWSTR     szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a827-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2a827-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="2a827-106">[v] Název modulu v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="2a827-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="2a827-107">Toto je pouze název souboru a ne název úplnou cestu.</span><span class="sxs-lookup"><span data-stu-id="2a827-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a827-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2a827-108">Requirements</span></span>  
 <span data-ttu-id="2a827-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a827-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a827-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2a827-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2a827-111">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2a827-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2a827-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a827-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a827-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a827-113">See Also</span></span>  
 [<span data-ttu-id="2a827-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2a827-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="2a827-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2a827-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
