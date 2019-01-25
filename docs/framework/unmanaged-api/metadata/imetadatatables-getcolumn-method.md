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
ms.openlocfilehash: a88acf59043613bb216ffe84dfb1593bd6ebea00
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651887"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="55b5b-102">IMetaDataTables::GetColumn – metoda</span><span class="sxs-lookup"><span data-stu-id="55b5b-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="55b5b-103">Získá ukazatel na hodnotě obsažené v buňce zadaný sloupců a řádků v dané tabulce.</span><span class="sxs-lookup"><span data-stu-id="55b5b-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55b5b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55b5b-104">Syntax</span></span>  
  
```  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55b5b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="55b5b-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="55b5b-106">[in] Index v tabulce.</span><span class="sxs-lookup"><span data-stu-id="55b5b-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="55b5b-107">[in] Index sloupce v tabulce.</span><span class="sxs-lookup"><span data-stu-id="55b5b-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="55b5b-108">[in] Index řádku v tabulce.</span><span class="sxs-lookup"><span data-stu-id="55b5b-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="55b5b-109">[out] Ukazatel na hodnotu v buňce.</span><span class="sxs-lookup"><span data-stu-id="55b5b-109">[out] A pointer to the value in the cell.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55b5b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="55b5b-110">Requirements</span></span>  
 <span data-ttu-id="55b5b-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55b5b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55b5b-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="55b5b-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="55b5b-113">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="55b5b-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="55b5b-114">**Verze rozhraní .NET framework** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55b5b-114">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55b5b-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55b5b-115">See also</span></span>
- [<span data-ttu-id="55b5b-116">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="55b5b-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="55b5b-117">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="55b5b-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
