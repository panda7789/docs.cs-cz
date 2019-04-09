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
ms.openlocfilehash: 6156499368fb743b69c03f38b40ad3c5bcabce6e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174899"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="56cd4-102">IMetaDataTables::GetColumnInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="56cd4-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="56cd4-103">Získá data o zadaný sloupec zadané tabulky.</span><span class="sxs-lookup"><span data-stu-id="56cd4-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56cd4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56cd4-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="56cd4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="56cd4-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="56cd4-106">[in] Index požadovanou tabulku.</span><span class="sxs-lookup"><span data-stu-id="56cd4-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="56cd4-107">[in] Index na požadovaný sloupec.</span><span class="sxs-lookup"><span data-stu-id="56cd4-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="56cd4-108">[out] Ukazatel na posun sloupce v řádku.</span><span class="sxs-lookup"><span data-stu-id="56cd4-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="56cd4-109">[out] Ukazatel na velikost v bajtech, ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="56cd4-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="56cd4-110">[out] Ukazatel na typ hodnoty ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="56cd4-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="56cd4-111">[out] Ukazatel na ukazatel na název sloupce.</span><span class="sxs-lookup"><span data-stu-id="56cd4-111">[out] A pointer to a pointer to the column name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56cd4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="56cd4-112">Requirements</span></span>  
 <span data-ttu-id="56cd4-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56cd4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56cd4-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="56cd4-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="56cd4-115">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="56cd4-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="56cd4-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="56cd4-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="56cd4-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56cd4-117">See also</span></span>

- [<span data-ttu-id="56cd4-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56cd4-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="56cd4-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56cd4-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
