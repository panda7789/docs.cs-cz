---
title: IMetaDataImport::GetModuleFromScope – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type:
- apiref
ms.openlocfilehash: 026a952e14cda2ef4ebc32ca91006026e920e3c1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437354"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="236a4-102">IMetaDataImport::GetModuleFromScope – metoda</span><span class="sxs-lookup"><span data-stu-id="236a4-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="236a4-103">Gets a metadata token for the module referenced in the current metadata scope.</span><span class="sxs-lookup"><span data-stu-id="236a4-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="236a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="236a4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="236a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="236a4-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="236a4-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span><span class="sxs-lookup"><span data-stu-id="236a4-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="236a4-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="236a4-107">Requirements</span></span>  
 <span data-ttu-id="236a4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="236a4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="236a4-109">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="236a4-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="236a4-110">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="236a4-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="236a4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="236a4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="236a4-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="236a4-112">See also</span></span>

- [<span data-ttu-id="236a4-113">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="236a4-113">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="236a4-114">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="236a4-114">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
