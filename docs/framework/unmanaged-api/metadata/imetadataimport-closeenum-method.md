---
title: IMetaDataImport::CloseEnum – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dda94acc2ec5da456cdc41ba0902cdc414b11524
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486378"
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="8b83d-102">IMetaDataImport::CloseEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="8b83d-102">IMetaDataImport::CloseEnum Method</span></span>
<span data-ttu-id="8b83d-103">Enumerátor, který je identifikován určený zavře.</span><span class="sxs-lookup"><span data-stu-id="8b83d-103">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b83d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b83d-104">Syntax</span></span>  
  
```  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b83d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b83d-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="8b83d-106">[in] Popisovač pro enumerátor zavřete.</span><span class="sxs-lookup"><span data-stu-id="8b83d-106">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b83d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b83d-107">Remarks</span></span>  
 <span data-ttu-id="8b83d-108">Popisovač určený `hEnum` se získávají z předchozí `Enum` *název* volání (například [imetadataimport::enumtypedefs –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="8b83d-108">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b83d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b83d-109">Requirements</span></span>  
 <span data-ttu-id="8b83d-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b83d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b83d-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8b83d-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b83d-112">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8b83d-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8b83d-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b83d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b83d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b83d-114">See also</span></span>
- [<span data-ttu-id="8b83d-115">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b83d-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8b83d-116">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b83d-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
