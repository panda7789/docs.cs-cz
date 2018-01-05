---
title: "IMetaDataTables::GetColumnInfo – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetColumnInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 48272219ee6a43006a76fddfd974275ac39b6e80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="c05fd-102">IMetaDataTables::GetColumnInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="c05fd-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="c05fd-103">Získá data o zadaný sloupec zadané tabulky.</span><span class="sxs-lookup"><span data-stu-id="c05fd-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c05fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c05fd-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="c05fd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c05fd-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="c05fd-106">[v] Index požadovanou tabulku.</span><span class="sxs-lookup"><span data-stu-id="c05fd-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="c05fd-107">[v] Index požadovaný sloupec.</span><span class="sxs-lookup"><span data-stu-id="c05fd-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="c05fd-108">[out] Ukazatel na posun sloupce v řádku.</span><span class="sxs-lookup"><span data-stu-id="c05fd-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="c05fd-109">[out] Ukazatel na velikost v bajtech sloupce.</span><span class="sxs-lookup"><span data-stu-id="c05fd-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="c05fd-110">[out] Ukazatel na typ hodnoty ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="c05fd-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="c05fd-111">[out] Ukazatel na ukazatel na název sloupce.</span><span class="sxs-lookup"><span data-stu-id="c05fd-111">[out] A pointer to a pointer to the column name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c05fd-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c05fd-112">Requirements</span></span>  
 <span data-ttu-id="c05fd-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c05fd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c05fd-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c05fd-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c05fd-115">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c05fd-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c05fd-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c05fd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c05fd-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="c05fd-117">See Also</span></span>  
 [<span data-ttu-id="c05fd-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c05fd-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="c05fd-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c05fd-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
