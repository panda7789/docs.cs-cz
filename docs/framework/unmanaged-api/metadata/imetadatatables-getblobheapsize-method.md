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
ms.openlocfilehash: c32407c3fc0bc5a045b80ec48937699826d981af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177165"
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="b70e7-102">IMetaDataTables::GetBlobHeapSize – metoda</span><span class="sxs-lookup"><span data-stu-id="b70e7-102">IMetaDataTables::GetBlobHeapSize Method</span></span>
<span data-ttu-id="b70e7-103">Získá velikost v bajtů haldy binární velký objekt (BLOB).</span><span class="sxs-lookup"><span data-stu-id="b70e7-103">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b70e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b70e7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="b70e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b70e7-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="b70e7-106">[out] Ukazatel na velikost haldy blob v bajtech.</span><span class="sxs-lookup"><span data-stu-id="b70e7-106">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b70e7-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b70e7-107">Requirements</span></span>  
 <span data-ttu-id="b70e7-108">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b70e7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b70e7-109">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="b70e7-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b70e7-110">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b70e7-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b70e7-111">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b70e7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b70e7-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="b70e7-112">See also</span></span>

- [<span data-ttu-id="b70e7-113">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b70e7-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="b70e7-114">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b70e7-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
