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
ms.openlocfilehash: a044924810016eea60682b8765aeee448b552f0d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501193"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="e263b-102">IMetaDataTables::GetColumnInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="e263b-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="e263b-103">Načte data o zadaném sloupci v zadané tabulce.</span><span class="sxs-lookup"><span data-stu-id="e263b-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e263b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e263b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e263b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e263b-105">Parameters</span></span>
=======

 `ixTbl`  
 <span data-ttu-id="e263b-106">pro Index požadované tabulky</span><span class="sxs-lookup"><span data-stu-id="e263b-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="e263b-107">pro Index požadovaného sloupce</span><span class="sxs-lookup"><span data-stu-id="e263b-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="e263b-108">mimo Ukazatel na posun sloupce v řádku.</span><span class="sxs-lookup"><span data-stu-id="e263b-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="e263b-109">mimo Ukazatel na velikost sloupce v bajtech.</span><span class="sxs-lookup"><span data-stu-id="e263b-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="e263b-110">mimo Ukazatel na typ hodnot ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="e263b-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="e263b-111">mimo Ukazatel na ukazatel na název sloupce.</span><span class="sxs-lookup"><span data-stu-id="e263b-111">[out] A pointer to a pointer to the column name.</span></span>  

## <a name="remarks"></a><span data-ttu-id="e263b-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e263b-112">Remarks</span></span>

<span data-ttu-id="e263b-113">Vrácený typ sloupce spadá do rozsahu hodnot:</span><span class="sxs-lookup"><span data-stu-id="e263b-113">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="e263b-114">pType</span><span class="sxs-lookup"><span data-stu-id="e263b-114">pType</span></span>                    | <span data-ttu-id="e263b-115">Description</span><span class="sxs-lookup"><span data-stu-id="e263b-115">Description</span></span>   | <span data-ttu-id="e263b-116">Pomocná funkce</span><span class="sxs-lookup"><span data-stu-id="e263b-116">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="e263b-117">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="e263b-117">`0`..`iRidMax`</span></span><br><span data-ttu-id="e263b-118">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="e263b-118">(0..63)</span></span>   | <span data-ttu-id="e263b-119">Mezinárodní</span><span class="sxs-lookup"><span data-stu-id="e263b-119">Rid</span></span>           | <span data-ttu-id="e263b-120">**IsRidType**</span><span class="sxs-lookup"><span data-stu-id="e263b-120">**IsRidType**</span></span><br><span data-ttu-id="e263b-121">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="e263b-121">**IsRidOrToken**</span></span> |
| <span data-ttu-id="e263b-122">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="e263b-122">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="e263b-123">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="e263b-123">(64..95)</span></span> | <span data-ttu-id="e263b-124">Kódovaný token</span><span class="sxs-lookup"><span data-stu-id="e263b-124">Coded token</span></span> | <span data-ttu-id="e263b-125">**IsCodedTokenType**</span><span class="sxs-lookup"><span data-stu-id="e263b-125">**IsCodedTokenType**</span></span> <br><span data-ttu-id="e263b-126">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="e263b-126">**IsRidOrToken**</span></span> |
| <span data-ttu-id="e263b-127">`iSHORT`(96)</span><span class="sxs-lookup"><span data-stu-id="e263b-127">`iSHORT` (96)</span></span>            | <span data-ttu-id="e263b-128">Int16</span><span class="sxs-lookup"><span data-stu-id="e263b-128">Int16</span></span>         | <span data-ttu-id="e263b-129">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="e263b-129">**IsFixedType**</span></span>                   |
| <span data-ttu-id="e263b-130">`iUSHORT`(97)</span><span class="sxs-lookup"><span data-stu-id="e263b-130">`iUSHORT` (97)</span></span>           | <span data-ttu-id="e263b-131">UInt16</span><span class="sxs-lookup"><span data-stu-id="e263b-131">UInt16</span></span>        | <span data-ttu-id="e263b-132">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="e263b-132">**IsFixedType**</span></span>                   |
| <span data-ttu-id="e263b-133">`iLONG`(98)</span><span class="sxs-lookup"><span data-stu-id="e263b-133">`iLONG` (98)</span></span>             | <span data-ttu-id="e263b-134">Int32</span><span class="sxs-lookup"><span data-stu-id="e263b-134">Int32</span></span>         | <span data-ttu-id="e263b-135">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="e263b-135">**IsFixedType**</span></span>                   |
| <span data-ttu-id="e263b-136">`iULONG`(99)</span><span class="sxs-lookup"><span data-stu-id="e263b-136">`iULONG` (99)</span></span>            | <span data-ttu-id="e263b-137">UInt32</span><span class="sxs-lookup"><span data-stu-id="e263b-137">UInt32</span></span>        | <span data-ttu-id="e263b-138">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="e263b-138">**IsFixedType**</span></span>                   |
| <span data-ttu-id="e263b-139">`iBYTE`(100)</span><span class="sxs-lookup"><span data-stu-id="e263b-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="e263b-140">Byte</span><span class="sxs-lookup"><span data-stu-id="e263b-140">Byte</span></span>          | <span data-ttu-id="e263b-141">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="e263b-141">**IsFixedType**</span></span>                   |
| <span data-ttu-id="e263b-142">`iSTRING`(101)</span><span class="sxs-lookup"><span data-stu-id="e263b-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="e263b-143">Řetězec</span><span class="sxs-lookup"><span data-stu-id="e263b-143">String</span></span>        | <span data-ttu-id="e263b-144">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="e263b-144">**IsHeapType**</span></span>                    |
| <span data-ttu-id="e263b-145">`iGUID`(102)</span><span class="sxs-lookup"><span data-stu-id="e263b-145">`iGUID` (102)</span></span>            | <span data-ttu-id="e263b-146">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="e263b-146">Guid</span></span>          | <span data-ttu-id="e263b-147">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="e263b-147">**IsHeapType**</span></span>                    |
| <span data-ttu-id="e263b-148">`iBLOB`(103)</span><span class="sxs-lookup"><span data-stu-id="e263b-148">`iBLOB` (103)</span></span>            | <span data-ttu-id="e263b-149">Objekt blob</span><span class="sxs-lookup"><span data-stu-id="e263b-149">Blob</span></span>          | <span data-ttu-id="e263b-150">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="e263b-150">**IsHeapType**</span></span>                    |

<span data-ttu-id="e263b-151">Hodnoty, které jsou uloženy v *haldě* (tj `IsHeapType == true` .), lze číst pomocí:</span><span class="sxs-lookup"><span data-stu-id="e263b-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="e263b-152">`iSTRING`: **IMetadataTables. GetString**</span><span class="sxs-lookup"><span data-stu-id="e263b-152">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="e263b-153">`iGUID`: **IMetadataTables. GETguid**</span><span class="sxs-lookup"><span data-stu-id="e263b-153">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="e263b-154">`iBLOB`: **IMetadataTables. Getblob**</span><span class="sxs-lookup"><span data-stu-id="e263b-154">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e263b-155">Chcete-li použít konstanty definované v tabulce výše, zahrňte direktivu, kterou `#define _DEFINE_META_DATA_META_CONSTANTS` poskytuje hlavičkový soubor *cor. h* .</span><span class="sxs-lookup"><span data-stu-id="e263b-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="e263b-156">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e263b-156">Requirements</span></span>  
 <span data-ttu-id="e263b-157">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e263b-157">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e263b-158">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e263b-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e263b-159">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="e263b-159">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e263b-160">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e263b-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e263b-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e263b-161">See also</span></span>

- [<span data-ttu-id="e263b-162">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e263b-162">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="e263b-163">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e263b-163">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
