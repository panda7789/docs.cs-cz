---
title: IMetaDataImport::CountEnum – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CountEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type:
- apiref
ms.openlocfilehash: 0c78ce8192d6456dd1b1be990d87b9209b028e09
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440366"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="ce3f1-102">IMetaDataImport::CountEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="ce3f1-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="ce3f1-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span><span class="sxs-lookup"><span data-stu-id="ce3f1-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce3f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce3f1-104">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,   
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce3f1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce3f1-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="ce3f1-106">[in] The handle for the enumerator.</span><span class="sxs-lookup"><span data-stu-id="ce3f1-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="ce3f1-107">[out] The number of elements enumerated.</span><span class="sxs-lookup"><span data-stu-id="ce3f1-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce3f1-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ce3f1-108">Remarks</span></span>  
 <span data-ttu-id="ce3f1-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="ce3f1-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce3f1-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ce3f1-110">Requirements</span></span>  
 <span data-ttu-id="ce3f1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce3f1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce3f1-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ce3f1-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ce3f1-113">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ce3f1-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ce3f1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce3f1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce3f1-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce3f1-115">See also</span></span>

- [<span data-ttu-id="ce3f1-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ce3f1-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ce3f1-117">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ce3f1-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
