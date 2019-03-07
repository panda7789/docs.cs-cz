---
title: IMetaDataTables::GetNextBlob – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextBlob
helpviewer_keywords:
- IMetaDataTables::GetNextBlob method [.NET Framework metadata]
- GetNextBlob method [.NET Framework metadata]
ms.assetid: 017c8ab4-4c09-4754-9935-5b0b49cabecb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e60ce044fc0272fbc9c4a641224bd70ad9faeeae
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488120"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="0d6e0-102">IMetaDataTables::GetNextBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="0d6e0-102">IMetaDataTables::GetNextBlob Method</span></span>
<span data-ttu-id="0d6e0-103">Získá index další binární velkých objektů (BLOB) v tabulce.</span><span class="sxs-lookup"><span data-stu-id="0d6e0-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d6e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d6e0-104">Syntax</span></span>  
  
```  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d6e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d6e0-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="0d6e0-106">[in] Index vrácená ze sloupce objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="0d6e0-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="0d6e0-107">[out] Ukazatel na index další objekt BLOB.</span><span class="sxs-lookup"><span data-stu-id="0d6e0-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d6e0-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0d6e0-108">Requirements</span></span>  
 <span data-ttu-id="0d6e0-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d6e0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d6e0-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0d6e0-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0d6e0-111">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0d6e0-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0d6e0-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d6e0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d6e0-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d6e0-113">See also</span></span>
- [<span data-ttu-id="0d6e0-114">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0d6e0-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="0d6e0-115">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0d6e0-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
