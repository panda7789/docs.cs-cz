---
title: "IMetaDataImport::CountEnum – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 26e826417e6fb48eb261278988bc7c351ee663aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="de5fa-102">IMetaDataImport::CountEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="de5fa-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="de5fa-103">Získá počet elementů ve výčtu, která byla načtena pomocí zadané enumerátor.</span><span class="sxs-lookup"><span data-stu-id="de5fa-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de5fa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de5fa-104">Syntax</span></span>  
  
```  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,   
   [out] ULONG       *pulCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de5fa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="de5fa-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="de5fa-106">[v] Popisovač pro enumerátor.</span><span class="sxs-lookup"><span data-stu-id="de5fa-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="de5fa-107">[out] Počet elementů ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="de5fa-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de5fa-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="de5fa-108">Remarks</span></span>  
 <span data-ttu-id="de5fa-109">Popisovač určený `hEnum` se získávají z předchozí `Enum` *název* volání (například [imetadataimport::enumtypedefs –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="de5fa-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de5fa-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="de5fa-110">Requirements</span></span>  
 <span data-ttu-id="de5fa-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de5fa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de5fa-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="de5fa-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="de5fa-113">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="de5fa-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="de5fa-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de5fa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de5fa-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="de5fa-115">See Also</span></span>  
 [<span data-ttu-id="de5fa-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="de5fa-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="de5fa-117">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="de5fa-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
