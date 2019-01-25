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
ms.openlocfilehash: 3f9f49219b810ac85b1f021c206bfab21d11a055
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745974"
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="f150e-102">IMetaDataTables::GetBlobHeapSize – metoda</span><span class="sxs-lookup"><span data-stu-id="f150e-102">IMetaDataTables::GetBlobHeapSize Method</span></span>
<span data-ttu-id="f150e-103">Získá velikost v bajtech haldy binárních rozsáhlých objektů (BLOB).</span><span class="sxs-lookup"><span data-stu-id="f150e-103">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f150e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f150e-104">Syntax</span></span>  
  
```  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="f150e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f150e-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="f150e-106">[out] Ukazatel na velikost v bajtech binárního rozsáhlého objektu haldy.</span><span class="sxs-lookup"><span data-stu-id="f150e-106">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f150e-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f150e-107">Requirements</span></span>  
 <span data-ttu-id="f150e-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f150e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f150e-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f150e-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f150e-110">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f150e-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f150e-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f150e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f150e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f150e-112">See also</span></span>
- [<span data-ttu-id="f150e-113">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f150e-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="f150e-114">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f150e-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
