---
title: IMetaDataTables::GetColumn – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9c380d363830eb6b4c47110d50cdb4d08e4568d8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499807"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="9bb95-102">IMetaDataTables::GetColumn – metoda</span><span class="sxs-lookup"><span data-stu-id="9bb95-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="9bb95-103">Získá ukazatel na hodnotě obsažené v buňce zadaný sloupců a řádků v dané tabulce.</span><span class="sxs-lookup"><span data-stu-id="9bb95-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bb95-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9bb95-104">Syntax</span></span>  
  
```  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9bb95-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9bb95-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="9bb95-106">[in] Index v tabulce.</span><span class="sxs-lookup"><span data-stu-id="9bb95-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="9bb95-107">[in] Index sloupce v tabulce.</span><span class="sxs-lookup"><span data-stu-id="9bb95-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="9bb95-108">[in] Index řádku v tabulce.</span><span class="sxs-lookup"><span data-stu-id="9bb95-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="9bb95-109">[out] Ukazatel na hodnotu v buňce.</span><span class="sxs-lookup"><span data-stu-id="9bb95-109">[out] A pointer to the value in the cell.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bb95-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9bb95-110">Requirements</span></span>  
 <span data-ttu-id="9bb95-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bb95-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bb95-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9bb95-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9bb95-113">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9bb95-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9bb95-114">**Verze rozhraní .NET framework** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bb95-114">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bb95-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9bb95-115">See also</span></span>
- [<span data-ttu-id="9bb95-116">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9bb95-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="9bb95-117">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9bb95-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
