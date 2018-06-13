---
title: IMetaDataTables::GetGuidHeapSize – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuidHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuidHeapSize
helpviewer_keywords:
- GetGuidHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetGuidHeapSize method [.NET Framework metadata]
ms.assetid: e875cbee-1ad9-4f1a-bf03-38cdb8ff371a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 97d196769b549022ce498958fc34cf08df442d0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447087"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="6217a-102">IMetaDataTables::GetGuidHeapSize – metoda</span><span class="sxs-lookup"><span data-stu-id="6217a-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="6217a-103">Získá velikost v bajtech haldě identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="6217a-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6217a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6217a-104">Syntax</span></span>  
  
```  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6217a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6217a-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="6217a-106">[out] Ukazatel na velikost v bajtech haldě identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="6217a-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6217a-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6217a-107">Requirements</span></span>  
 <span data-ttu-id="6217a-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6217a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6217a-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6217a-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6217a-110">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6217a-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6217a-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6217a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6217a-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="6217a-112">See Also</span></span>  
 [<span data-ttu-id="6217a-113">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6217a-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="6217a-114">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6217a-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
