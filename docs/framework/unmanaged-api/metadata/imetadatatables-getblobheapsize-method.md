---
title: IMetaDataTables::GetBlobHeapSize – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlobHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlobHeapSize
helpviewer_keywords:
- GetBlobHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetBlobHeapSize method [.NET Framework metadata]
ms.assetid: 6330a9ee-8cd5-4299-86f1-b4de2c701a0d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 787ea506c6698925473175cf7fdac340c0c2eca8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447271"
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="28c4a-102">IMetaDataTables::GetBlobHeapSize – metoda</span><span class="sxs-lookup"><span data-stu-id="28c4a-102">IMetaDataTables::GetBlobHeapSize Method</span></span>
<span data-ttu-id="28c4a-103">Získá velikost v bajtech haldě binární rozsáhlý objekt (binární rozsáhlý OBJEKT).</span><span class="sxs-lookup"><span data-stu-id="28c4a-103">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28c4a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28c4a-104">Syntax</span></span>  
  
```  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="28c4a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="28c4a-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="28c4a-106">[out] Ukazatel na velikost v bajtech haldě objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="28c4a-106">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28c4a-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="28c4a-107">Requirements</span></span>  
 <span data-ttu-id="28c4a-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28c4a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28c4a-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="28c4a-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="28c4a-110">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="28c4a-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="28c4a-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28c4a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28c4a-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="28c4a-112">See Also</span></span>  
 [<span data-ttu-id="28c4a-113">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28c4a-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="28c4a-114">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28c4a-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
