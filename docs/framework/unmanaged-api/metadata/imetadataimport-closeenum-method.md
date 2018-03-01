---
title: "IMetaDataImport::CloseEnum – metoda"
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
- IMetaDataImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CloseEnum
helpviewer_keywords:
- IMetaDataImport::CloseEnum method [.NET Framework metadata]
- CloseEnum method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 727819d5-1dab-4ebb-ac25-950b4111dc72
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 013629b5a3389fcb8da9368f7875bd1977ee9e20
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="fe56c-102">IMetaDataImport::CloseEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="fe56c-102">IMetaDataImport::CloseEnum Method</span></span>
<span data-ttu-id="fe56c-103">Zavře enumerátor, který je zadaný popisovač identifikována.</span><span class="sxs-lookup"><span data-stu-id="fe56c-103">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe56c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe56c-104">Syntax</span></span>  
  
```  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe56c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe56c-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="fe56c-106">[v] Popisovač pro enumerátor zavřete.</span><span class="sxs-lookup"><span data-stu-id="fe56c-106">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe56c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe56c-107">Remarks</span></span>  
 <span data-ttu-id="fe56c-108">Popisovač určený `hEnum` se získávají z předchozí `Enum` *název* volání (například [imetadataimport::enumtypedefs –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="fe56c-108">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe56c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe56c-109">Requirements</span></span>  
 <span data-ttu-id="fe56c-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe56c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe56c-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fe56c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fe56c-112">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fe56c-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fe56c-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe56c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe56c-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe56c-114">See Also</span></span>  
 [<span data-ttu-id="fe56c-115">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fe56c-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="fe56c-116">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fe56c-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
