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
ms.openlocfilehash: 7f27955467436d562c6a9acc9d7f666427e4c85b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770711"
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="2df84-102">IMetaDataImport::CloseEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="2df84-102">IMetaDataImport::CloseEnum Method</span></span>
<span data-ttu-id="2df84-103">Enumerátor, který je identifikován určený zavře.</span><span class="sxs-lookup"><span data-stu-id="2df84-103">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2df84-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2df84-104">Syntax</span></span>  
  
```cpp  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2df84-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2df84-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="2df84-106">[in] Popisovač pro enumerátor zavřete.</span><span class="sxs-lookup"><span data-stu-id="2df84-106">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2df84-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2df84-107">Remarks</span></span>  
 <span data-ttu-id="2df84-108">Popisovač určený `hEnum` se získávají z předchozí `Enum` *název* volání (například [imetadataimport::enumtypedefs –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="2df84-108">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2df84-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2df84-109">Requirements</span></span>  
 <span data-ttu-id="2df84-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2df84-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2df84-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2df84-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2df84-112">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2df84-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2df84-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2df84-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2df84-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2df84-114">See also</span></span>

- [<span data-ttu-id="2df84-115">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2df84-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="2df84-116">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2df84-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
