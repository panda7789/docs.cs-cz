---
title: IMetaDataTables::GetColumnInfo – metoda
ms.date: 10/10/2019
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
ms.openlocfilehash: cc8aac32149fed952737d928e16a8f6efc448c79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177125"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="457af-102">IMetaDataTables::GetColumnInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="457af-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="457af-103">Získá data o zadaném sloupci v zadané tabulce.</span><span class="sxs-lookup"><span data-stu-id="457af-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="457af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="457af-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumnInfo (
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="457af-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="457af-105">Parameters</span></span>
=======

 `ixTbl`  
 <span data-ttu-id="457af-106">[v] Index požadované tabulky.</span><span class="sxs-lookup"><span data-stu-id="457af-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="457af-107">[v] Index požadovaného sloupce.</span><span class="sxs-lookup"><span data-stu-id="457af-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="457af-108">[out] Ukazatel na posun sloupce v řádku.</span><span class="sxs-lookup"><span data-stu-id="457af-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="457af-109">[out] Ukazatel na velikost sloupce v bajtech.</span><span class="sxs-lookup"><span data-stu-id="457af-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="457af-110">[out] Ukazatel na typ hodnot ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="457af-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="457af-111">[out] Ukazatel na ukazatel na název sloupce.</span><span class="sxs-lookup"><span data-stu-id="457af-111">[out] A pointer to a pointer to the column name.</span></span>  

## <a name="remarks"></a><span data-ttu-id="457af-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="457af-112">Remarks</span></span>

<span data-ttu-id="457af-113">Typ vráceného sloupce spadá do rozsahu hodnot:</span><span class="sxs-lookup"><span data-stu-id="457af-113">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="457af-114">pTyp</span><span class="sxs-lookup"><span data-stu-id="457af-114">pType</span></span>                    | <span data-ttu-id="457af-115">Popis</span><span class="sxs-lookup"><span data-stu-id="457af-115">Description</span></span>   | <span data-ttu-id="457af-116">Pomocná funkce</span><span class="sxs-lookup"><span data-stu-id="457af-116">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="457af-117">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="457af-117">`0`..`iRidMax`</span></span><br><span data-ttu-id="457af-118">(0..63)</span><span class="sxs-lookup"><span data-stu-id="457af-118">(0..63)</span></span>   | <span data-ttu-id="457af-119">Zbavit</span><span class="sxs-lookup"><span data-stu-id="457af-119">Rid</span></span>           | <span data-ttu-id="457af-120">**ISRIDTyp**</span><span class="sxs-lookup"><span data-stu-id="457af-120">**IsRidType**</span></span><br><span data-ttu-id="457af-121">**Isridortoken**</span><span class="sxs-lookup"><span data-stu-id="457af-121">**IsRidOrToken**</span></span> |
| <span data-ttu-id="457af-122">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="457af-122">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="457af-123">(64..95)</span><span class="sxs-lookup"><span data-stu-id="457af-123">(64..95)</span></span> | <span data-ttu-id="457af-124">Kódovaný token</span><span class="sxs-lookup"><span data-stu-id="457af-124">Coded token</span></span> | <span data-ttu-id="457af-125">**IsCodedTokenType**</span><span class="sxs-lookup"><span data-stu-id="457af-125">**IsCodedTokenType**</span></span> <br><span data-ttu-id="457af-126">**Isridortoken**</span><span class="sxs-lookup"><span data-stu-id="457af-126">**IsRidOrToken**</span></span> |
| <span data-ttu-id="457af-127">`iSHORT`(96)</span><span class="sxs-lookup"><span data-stu-id="457af-127">`iSHORT` (96)</span></span>            | <span data-ttu-id="457af-128">Int16</span><span class="sxs-lookup"><span data-stu-id="457af-128">Int16</span></span>         | <span data-ttu-id="457af-129">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="457af-129">**IsFixedType**</span></span>                   |
| <span data-ttu-id="457af-130">`iUSHORT`(97)</span><span class="sxs-lookup"><span data-stu-id="457af-130">`iUSHORT` (97)</span></span>           | <span data-ttu-id="457af-131">UInt16</span><span class="sxs-lookup"><span data-stu-id="457af-131">UInt16</span></span>        | <span data-ttu-id="457af-132">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="457af-132">**IsFixedType**</span></span>                   |
| <span data-ttu-id="457af-133">`iLONG`(98)</span><span class="sxs-lookup"><span data-stu-id="457af-133">`iLONG` (98)</span></span>             | <span data-ttu-id="457af-134">Int32</span><span class="sxs-lookup"><span data-stu-id="457af-134">Int32</span></span>         | <span data-ttu-id="457af-135">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="457af-135">**IsFixedType**</span></span>                   |
| <span data-ttu-id="457af-136">`iULONG`(99)</span><span class="sxs-lookup"><span data-stu-id="457af-136">`iULONG` (99)</span></span>            | <span data-ttu-id="457af-137">UInt32</span><span class="sxs-lookup"><span data-stu-id="457af-137">UInt32</span></span>        | <span data-ttu-id="457af-138">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="457af-138">**IsFixedType**</span></span>                   |
| <span data-ttu-id="457af-139">`iBYTE`(100)</span><span class="sxs-lookup"><span data-stu-id="457af-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="457af-140">Byte</span><span class="sxs-lookup"><span data-stu-id="457af-140">Byte</span></span>          | <span data-ttu-id="457af-141">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="457af-141">**IsFixedType**</span></span>                   |
| <span data-ttu-id="457af-142">`iSTRING`(101)</span><span class="sxs-lookup"><span data-stu-id="457af-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="457af-143">Řetězec</span><span class="sxs-lookup"><span data-stu-id="457af-143">String</span></span>        | <span data-ttu-id="457af-144">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="457af-144">**IsHeapType**</span></span>                    |
| <span data-ttu-id="457af-145">`iGUID`(102)</span><span class="sxs-lookup"><span data-stu-id="457af-145">`iGUID` (102)</span></span>            | <span data-ttu-id="457af-146">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="457af-146">Guid</span></span>          | <span data-ttu-id="457af-147">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="457af-147">**IsHeapType**</span></span>                    |
| <span data-ttu-id="457af-148">`iBLOB`(103)</span><span class="sxs-lookup"><span data-stu-id="457af-148">`iBLOB` (103)</span></span>            | <span data-ttu-id="457af-149">Objekt blob</span><span class="sxs-lookup"><span data-stu-id="457af-149">Blob</span></span>          | <span data-ttu-id="457af-150">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="457af-150">**IsHeapType**</span></span>                    |

<span data-ttu-id="457af-151">Hodnoty, které jsou uloženy v `IsHeapType == true` *haldě* (to znamená) lze číst pomocí:</span><span class="sxs-lookup"><span data-stu-id="457af-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="457af-152">`iSTRING`: **IMetadataTables.GetString**</span><span class="sxs-lookup"><span data-stu-id="457af-152">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="457af-153">`iGUID`: **IMetadataTables.GetGUID**</span><span class="sxs-lookup"><span data-stu-id="457af-153">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="457af-154">`iBLOB`: **IMetadataTables.GetBlob**</span><span class="sxs-lookup"><span data-stu-id="457af-154">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="457af-155">Chcete-li použít konstanty definované v tabulce `#define _DEFINE_META_DATA_META_CONSTANTS` výše, zadejte direktivu poskytnutou souborem záhlaví *cor.h.*</span><span class="sxs-lookup"><span data-stu-id="457af-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="457af-156">Požadavky</span><span class="sxs-lookup"><span data-stu-id="457af-156">Requirements</span></span>  
 <span data-ttu-id="457af-157">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="457af-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="457af-158">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="457af-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="457af-159">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="457af-159">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="457af-160">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="457af-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="457af-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="457af-161">See also</span></span>

- [<span data-ttu-id="457af-162">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="457af-162">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="457af-163">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="457af-163">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
