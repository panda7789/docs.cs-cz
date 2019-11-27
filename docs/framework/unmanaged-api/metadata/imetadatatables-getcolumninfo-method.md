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
ms.openlocfilehash: 854d3ad28cc00c03e903b9e1d2ce3863e3ceef17
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436103"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="d8b56-102">IMetaDataTables::GetColumnInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="d8b56-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="d8b56-103">Načte data o zadaném sloupci v zadané tabulce.</span><span class="sxs-lookup"><span data-stu-id="d8b56-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8b56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8b56-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d8b56-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8b56-105">Parameters</span></span>
=======

 `ixTbl`  
 <span data-ttu-id="d8b56-106">pro Index požadované tabulky</span><span class="sxs-lookup"><span data-stu-id="d8b56-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="d8b56-107">pro Index požadovaného sloupce</span><span class="sxs-lookup"><span data-stu-id="d8b56-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="d8b56-108">mimo Ukazatel na posun sloupce v řádku.</span><span class="sxs-lookup"><span data-stu-id="d8b56-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="d8b56-109">mimo Ukazatel na velikost sloupce v bajtech.</span><span class="sxs-lookup"><span data-stu-id="d8b56-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="d8b56-110">mimo Ukazatel na typ hodnot ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="d8b56-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="d8b56-111">mimo Ukazatel na ukazatel na název sloupce.</span><span class="sxs-lookup"><span data-stu-id="d8b56-111">[out] A pointer to a pointer to the column name.</span></span>  
 
## <a name="remarks"></a><span data-ttu-id="d8b56-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8b56-112">Remarks</span></span>

<span data-ttu-id="d8b56-113">Vrácený typ sloupce spadá do rozsahu hodnot:</span><span class="sxs-lookup"><span data-stu-id="d8b56-113">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="d8b56-114">pType</span><span class="sxs-lookup"><span data-stu-id="d8b56-114">pType</span></span>                    | <span data-ttu-id="d8b56-115">Popis</span><span class="sxs-lookup"><span data-stu-id="d8b56-115">Description</span></span>   | <span data-ttu-id="d8b56-116">Pomocná funkce</span><span class="sxs-lookup"><span data-stu-id="d8b56-116">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="d8b56-117">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="d8b56-117">`0`..`iRidMax`</span></span><br><span data-ttu-id="d8b56-118">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="d8b56-118">(0..63)</span></span>   | <span data-ttu-id="d8b56-119">Mezinárodní</span><span class="sxs-lookup"><span data-stu-id="d8b56-119">Rid</span></span>           | <span data-ttu-id="d8b56-120">**IsRidType**</span><span class="sxs-lookup"><span data-stu-id="d8b56-120">**IsRidType**</span></span><br><span data-ttu-id="d8b56-121">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="d8b56-121">**IsRidOrToken**</span></span> |
| <span data-ttu-id="d8b56-122">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="d8b56-122">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="d8b56-123">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="d8b56-123">(64..95)</span></span> | <span data-ttu-id="d8b56-124">Kódovaný token</span><span class="sxs-lookup"><span data-stu-id="d8b56-124">Coded token</span></span> | <span data-ttu-id="d8b56-125">**IsCodedTokenType**</span><span class="sxs-lookup"><span data-stu-id="d8b56-125">**IsCodedTokenType**</span></span> <br><span data-ttu-id="d8b56-126">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="d8b56-126">**IsRidOrToken**</span></span> |
| <span data-ttu-id="d8b56-127">`iSHORT` (96)</span><span class="sxs-lookup"><span data-stu-id="d8b56-127">`iSHORT` (96)</span></span>            | <span data-ttu-id="d8b56-128">Int16</span><span class="sxs-lookup"><span data-stu-id="d8b56-128">Int16</span></span>         | <span data-ttu-id="d8b56-129">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="d8b56-129">**IsFixedType**</span></span>                   |
| <span data-ttu-id="d8b56-130">`iUSHORT` (97)</span><span class="sxs-lookup"><span data-stu-id="d8b56-130">`iUSHORT` (97)</span></span>           | <span data-ttu-id="d8b56-131">UInt16</span><span class="sxs-lookup"><span data-stu-id="d8b56-131">UInt16</span></span>        | <span data-ttu-id="d8b56-132">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="d8b56-132">**IsFixedType**</span></span>                   |
| <span data-ttu-id="d8b56-133">`iLONG` (98)</span><span class="sxs-lookup"><span data-stu-id="d8b56-133">`iLONG` (98)</span></span>             | <span data-ttu-id="d8b56-134">Datový typ Int32</span><span class="sxs-lookup"><span data-stu-id="d8b56-134">Int32</span></span>         | <span data-ttu-id="d8b56-135">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="d8b56-135">**IsFixedType**</span></span>                   |
| <span data-ttu-id="d8b56-136">`iULONG` (99)</span><span class="sxs-lookup"><span data-stu-id="d8b56-136">`iULONG` (99)</span></span>            | <span data-ttu-id="d8b56-137">UInt32</span><span class="sxs-lookup"><span data-stu-id="d8b56-137">UInt32</span></span>        | <span data-ttu-id="d8b56-138">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="d8b56-138">**IsFixedType**</span></span>                   |
| <span data-ttu-id="d8b56-139">`iBYTE` (100)</span><span class="sxs-lookup"><span data-stu-id="d8b56-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="d8b56-140">Byte</span><span class="sxs-lookup"><span data-stu-id="d8b56-140">Byte</span></span>          | <span data-ttu-id="d8b56-141">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="d8b56-141">**IsFixedType**</span></span>                   |
| <span data-ttu-id="d8b56-142">`iSTRING` (101)</span><span class="sxs-lookup"><span data-stu-id="d8b56-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="d8b56-143">String</span><span class="sxs-lookup"><span data-stu-id="d8b56-143">String</span></span>        | <span data-ttu-id="d8b56-144">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="d8b56-144">**IsHeapType**</span></span>                    |
| <span data-ttu-id="d8b56-145">`iGUID` (102)</span><span class="sxs-lookup"><span data-stu-id="d8b56-145">`iGUID` (102)</span></span>            | <span data-ttu-id="d8b56-146">identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="d8b56-146">Guid</span></span>          | <span data-ttu-id="d8b56-147">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="d8b56-147">**IsHeapType**</span></span>                    |
| <span data-ttu-id="d8b56-148">`iBLOB` (103)</span><span class="sxs-lookup"><span data-stu-id="d8b56-148">`iBLOB` (103)</span></span>            | <span data-ttu-id="d8b56-149">Blob</span><span class="sxs-lookup"><span data-stu-id="d8b56-149">Blob</span></span>          | <span data-ttu-id="d8b56-150">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="d8b56-150">**IsHeapType**</span></span>                    |

<span data-ttu-id="d8b56-151">Hodnoty, které jsou uloženy v *haldě* (to znamená `IsHeapType == true`), lze číst pomocí:</span><span class="sxs-lookup"><span data-stu-id="d8b56-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="d8b56-152">`iSTRING`: **IMetadataTables. GetString**</span><span class="sxs-lookup"><span data-stu-id="d8b56-152">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="d8b56-153">`iGUID`: **IMetadataTables. GETguid**</span><span class="sxs-lookup"><span data-stu-id="d8b56-153">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="d8b56-154">`iBLOB`: **IMetadataTables. Getblob**</span><span class="sxs-lookup"><span data-stu-id="d8b56-154">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8b56-155">Chcete-li použít konstanty definované v tabulce výše, zahrňte direktivu `#define _DEFINE_META_DATA_META_CONSTANTS` poskytnutou hlavičkovým souborem *cor. h* .</span><span class="sxs-lookup"><span data-stu-id="d8b56-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="d8b56-156">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8b56-156">Requirements</span></span>  
 <span data-ttu-id="d8b56-157">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8b56-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8b56-158">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d8b56-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d8b56-159">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="d8b56-159">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d8b56-160">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8b56-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8b56-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8b56-161">See also</span></span>

- [<span data-ttu-id="d8b56-162">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d8b56-162">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="d8b56-163">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d8b56-163">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
