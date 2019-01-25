---
title: IMetaDataTables::GetColumnInfo – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetColumnInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 245933b23028e2baf8a09ca07595f394b65c0ec3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698294"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="6f710-102">IMetaDataTables::GetColumnInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="6f710-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="6f710-103">Získá data o zadaný sloupec zadané tabulky.</span><span class="sxs-lookup"><span data-stu-id="6f710-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f710-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f710-104">Syntax</span></span>  
  
```  
HRESULT GetColumnInfo (   
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f710-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f710-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="6f710-106">[in] Index požadovanou tabulku.</span><span class="sxs-lookup"><span data-stu-id="6f710-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="6f710-107">[in] Index na požadovaný sloupec.</span><span class="sxs-lookup"><span data-stu-id="6f710-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="6f710-108">[out] Ukazatel na posun sloupce v řádku.</span><span class="sxs-lookup"><span data-stu-id="6f710-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="6f710-109">[out] Ukazatel na velikost v bajtech, ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="6f710-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="6f710-110">[out] Ukazatel na typ hodnoty ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="6f710-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="6f710-111">[out] Ukazatel na ukazatel na název sloupce.</span><span class="sxs-lookup"><span data-stu-id="6f710-111">[out] A pointer to a pointer to the column name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f710-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f710-112">Requirements</span></span>  
 <span data-ttu-id="6f710-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f710-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f710-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6f710-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6f710-115">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6f710-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6f710-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f710-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f710-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6f710-117">See also</span></span>
- [<span data-ttu-id="6f710-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f710-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="6f710-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f710-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
