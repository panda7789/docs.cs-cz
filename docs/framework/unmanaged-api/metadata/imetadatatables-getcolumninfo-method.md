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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dd67d9faafedf4fb92c69618d4464ebb2ce47dcc
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774249"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="30726-102">IMetaDataTables::GetColumnInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="30726-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="30726-103">Načte data o zadaném sloupci v zadané tabulce.</span><span class="sxs-lookup"><span data-stu-id="30726-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30726-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30726-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="30726-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="30726-105">Parameters</span></span>
=======

 `ixTbl`  
 <span data-ttu-id="30726-106">pro Index požadované tabulky</span><span class="sxs-lookup"><span data-stu-id="30726-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="30726-107">pro Index požadovaného sloupce</span><span class="sxs-lookup"><span data-stu-id="30726-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="30726-108">mimo Ukazatel na posun sloupce v řádku.</span><span class="sxs-lookup"><span data-stu-id="30726-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="30726-109">mimo Ukazatel na velikost sloupce v bajtech.</span><span class="sxs-lookup"><span data-stu-id="30726-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="30726-110">mimo Ukazatel na typ hodnot ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="30726-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="30726-111">mimo Ukazatel na ukazatel na název sloupce.</span><span class="sxs-lookup"><span data-stu-id="30726-111">[out] A pointer to a pointer to the column name.</span></span>  
 
## <a name="remarks"></a><span data-ttu-id="30726-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30726-112">Remarks</span></span>

<span data-ttu-id="30726-113">Vrácený typ sloupce spadá do rozsahu hodnot:</span><span class="sxs-lookup"><span data-stu-id="30726-113">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="30726-114">pType</span><span class="sxs-lookup"><span data-stu-id="30726-114">pType</span></span>                    | <span data-ttu-id="30726-115">Popis</span><span class="sxs-lookup"><span data-stu-id="30726-115">Description</span></span>   | <span data-ttu-id="30726-116">Pomocná funkce</span><span class="sxs-lookup"><span data-stu-id="30726-116">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="30726-117">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="30726-117">`0`..`iRidMax`</span></span><br><span data-ttu-id="30726-118">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="30726-118">(0..63)</span></span>   | <span data-ttu-id="30726-119">Mezinárodní</span><span class="sxs-lookup"><span data-stu-id="30726-119">Rid</span></span>           | <span data-ttu-id="30726-120">**IsRidType**</span><span class="sxs-lookup"><span data-stu-id="30726-120">**IsRidType**</span></span><br><span data-ttu-id="30726-121">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="30726-121">**IsRidOrToken**</span></span> |
| <span data-ttu-id="30726-122">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="30726-122">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="30726-123">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="30726-123">(64..95)</span></span> | <span data-ttu-id="30726-124">Kódovaný token</span><span class="sxs-lookup"><span data-stu-id="30726-124">Coded token</span></span> | <span data-ttu-id="30726-125">**IsCodedTokenType**</span><span class="sxs-lookup"><span data-stu-id="30726-125">**IsCodedTokenType**</span></span> <br><span data-ttu-id="30726-126">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="30726-126">**IsRidOrToken**</span></span> |
| <span data-ttu-id="30726-127">`iSHORT` (96)</span><span class="sxs-lookup"><span data-stu-id="30726-127">`iSHORT` (96)</span></span>            | <span data-ttu-id="30726-128">Int16</span><span class="sxs-lookup"><span data-stu-id="30726-128">Int16</span></span>         | <span data-ttu-id="30726-129">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="30726-129">**IsFixedType**</span></span>                   |
| <span data-ttu-id="30726-130">`iUSHORT` (97)</span><span class="sxs-lookup"><span data-stu-id="30726-130">`iUSHORT` (97)</span></span>           | <span data-ttu-id="30726-131">UInt16</span><span class="sxs-lookup"><span data-stu-id="30726-131">UInt16</span></span>        | <span data-ttu-id="30726-132">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="30726-132">**IsFixedType**</span></span>                   |
| <span data-ttu-id="30726-133">`iLONG` (98)</span><span class="sxs-lookup"><span data-stu-id="30726-133">`iLONG` (98)</span></span>             | <span data-ttu-id="30726-134">Int32</span><span class="sxs-lookup"><span data-stu-id="30726-134">Int32</span></span>         | <span data-ttu-id="30726-135">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="30726-135">**IsFixedType**</span></span>                   |
| <span data-ttu-id="30726-136">`iULONG` (99)</span><span class="sxs-lookup"><span data-stu-id="30726-136">`iULONG` (99)</span></span>            | <span data-ttu-id="30726-137">UInt32</span><span class="sxs-lookup"><span data-stu-id="30726-137">UInt32</span></span>        | <span data-ttu-id="30726-138">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="30726-138">**IsFixedType**</span></span>                   |
| <span data-ttu-id="30726-139">`iBYTE` (100)</span><span class="sxs-lookup"><span data-stu-id="30726-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="30726-140">Byte</span><span class="sxs-lookup"><span data-stu-id="30726-140">Byte</span></span>          | <span data-ttu-id="30726-141">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="30726-141">**IsFixedType**</span></span>                   |
| <span data-ttu-id="30726-142">`iSTRING` (101)</span><span class="sxs-lookup"><span data-stu-id="30726-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="30726-143">String</span><span class="sxs-lookup"><span data-stu-id="30726-143">String</span></span>        | <span data-ttu-id="30726-144">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="30726-144">**IsHeapType**</span></span>                    |
| <span data-ttu-id="30726-145">`iGUID` (102)</span><span class="sxs-lookup"><span data-stu-id="30726-145">`iGUID` (102)</span></span>            | <span data-ttu-id="30726-146">Hlavních</span><span class="sxs-lookup"><span data-stu-id="30726-146">Guid</span></span>          | <span data-ttu-id="30726-147">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="30726-147">**IsHeapType**</span></span>                    |
| <span data-ttu-id="30726-148">`iBLOB` (103)</span><span class="sxs-lookup"><span data-stu-id="30726-148">`iBLOB` (103)</span></span>            | <span data-ttu-id="30726-149">Příznaky</span><span class="sxs-lookup"><span data-stu-id="30726-149">Blob</span></span>          | <span data-ttu-id="30726-150">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="30726-150">**IsHeapType**</span></span>                    |

<span data-ttu-id="30726-151">Hodnoty, které jsou uloženy v *haldě* (to znamená `IsHeapType == true`), lze číst pomocí:</span><span class="sxs-lookup"><span data-stu-id="30726-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="30726-152">`iSTRING`: **IMetadataTables. GetString**</span><span class="sxs-lookup"><span data-stu-id="30726-152">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="30726-153">`iGUID`: **IMetadataTables. GETguid**</span><span class="sxs-lookup"><span data-stu-id="30726-153">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="30726-154">`iBLOB`: **IMetadataTables. Getblob**</span><span class="sxs-lookup"><span data-stu-id="30726-154">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30726-155">Chcete-li použít konstanty definované v tabulce výše, zahrňte direktivu `#define _DEFINE_META_DATA_META_CONSTANTS` poskytnutou hlavičkovým souborem *cor. h* .</span><span class="sxs-lookup"><span data-stu-id="30726-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="30726-156">Požadavky</span><span class="sxs-lookup"><span data-stu-id="30726-156">Requirements</span></span>  
 <span data-ttu-id="30726-157">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30726-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30726-158">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="30726-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="30726-159">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="30726-159">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="30726-160">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30726-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30726-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30726-161">See also</span></span>

- [<span data-ttu-id="30726-162">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="30726-162">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="30726-163">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="30726-163">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
