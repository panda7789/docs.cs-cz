---
title: IMetaDataTables::GetColumn – metoda
ms.date: 02/25/2019
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
ms.openlocfilehash: f43d4d1547cbe92f325950e1697dada83b42c4f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177141"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="d1768-102">IMetaDataTables::GetColumn – metoda</span><span class="sxs-lookup"><span data-stu-id="d1768-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="d1768-103">Získá ukazatel na hodnotu obsaženou v buňce zadaného sloupce a řádku v dané tabulce.</span><span class="sxs-lookup"><span data-stu-id="d1768-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1768-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1768-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumn (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1768-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1768-105">Parameters</span></span>

 `ixTbl`  
 <span data-ttu-id="d1768-106">[v] Index tabulky.</span><span class="sxs-lookup"><span data-stu-id="d1768-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="d1768-107">[v] Index sloupce v tabulce.</span><span class="sxs-lookup"><span data-stu-id="d1768-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="d1768-108">[v] Index řádku v tabulce.</span><span class="sxs-lookup"><span data-stu-id="d1768-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="d1768-109">[out] Ukazatel na hodnotu v buňce.</span><span class="sxs-lookup"><span data-stu-id="d1768-109">[out] A pointer to the value in the cell.</span></span>  

## <a name="remarks"></a><span data-ttu-id="d1768-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d1768-110">Remarks</span></span>

<span data-ttu-id="d1768-111">Interpretace hodnoty vrácené prostřednictvím `pVal` závisí na typu sloupce.</span><span class="sxs-lookup"><span data-stu-id="d1768-111">The interpretion of the value returned through `pVal` depends on the column's type.</span></span> <span data-ttu-id="d1768-112">Typ sloupce lze určit voláním [iMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="d1768-112">The column type can be determined by calling [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span></span>

- <span data-ttu-id="d1768-113">Metoda **GetColumn** automaticky převede sloupce typu **Rid** nebo **CodedToken** na plné 32bitové `mdToken` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d1768-113">The **GetColumn** method automatically converts columns of type **Rid** or **CodedToken** to full 32-bit `mdToken` values.</span></span>
- <span data-ttu-id="d1768-114">Také automaticky převede 8bitové nebo 16bitové hodnoty na plné 32bitové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d1768-114">It also automatically converts 8-bit or 16-bit values to full 32-bit values.</span></span>
- <span data-ttu-id="d1768-115">Pro sloupce typu *haldy* vrácené *pVal* bude index do odpovídající haldy.</span><span class="sxs-lookup"><span data-stu-id="d1768-115">For *heap* type columns, the returned *pVal* will be an index into the corresponding heap.</span></span>

| <span data-ttu-id="d1768-116">Typ sloupce</span><span class="sxs-lookup"><span data-stu-id="d1768-116">Column type</span></span>              | <span data-ttu-id="d1768-117">pVal obsahuje</span><span class="sxs-lookup"><span data-stu-id="d1768-117">pVal contains</span></span> | <span data-ttu-id="d1768-118">Poznámka</span><span class="sxs-lookup"><span data-stu-id="d1768-118">Comment</span></span>                          |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="d1768-119">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="d1768-119">`0`..`iRidMax`</span></span><br><span data-ttu-id="d1768-120">(0..63)</span><span class="sxs-lookup"><span data-stu-id="d1768-120">(0..63)</span></span>  | <span data-ttu-id="d1768-121">mdToken</span><span class="sxs-lookup"><span data-stu-id="d1768-121">mdToken</span></span>     | <span data-ttu-id="d1768-122">*pVal* bude obsahovat úplný token.</span><span class="sxs-lookup"><span data-stu-id="d1768-122">*pVal* will contain a full Token.</span></span> <span data-ttu-id="d1768-123">Funkce automaticky převede Rid do úplného tokenu.</span><span class="sxs-lookup"><span data-stu-id="d1768-123">The function automatically converts the Rid into a full token.</span></span> |
| <span data-ttu-id="d1768-124">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="d1768-124">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="d1768-125">(64..95)</span><span class="sxs-lookup"><span data-stu-id="d1768-125">(64..95)</span></span> | <span data-ttu-id="d1768-126">mdToken</span><span class="sxs-lookup"><span data-stu-id="d1768-126">mdToken</span></span> | <span data-ttu-id="d1768-127">Po návratu bude *pVal* obsahovat úplný token.</span><span class="sxs-lookup"><span data-stu-id="d1768-127">Upon return, *pVal* will contain a full Token.</span></span> <span data-ttu-id="d1768-128">Funkce automaticky dekomprimuje CodedToken do úplného tokenu.</span><span class="sxs-lookup"><span data-stu-id="d1768-128">The function automatically decompresses the CodedToken into a full token.</span></span> |
| <span data-ttu-id="d1768-129">`iSHORT`(96)</span><span class="sxs-lookup"><span data-stu-id="d1768-129">`iSHORT` (96)</span></span>            | <span data-ttu-id="d1768-130">Int16</span><span class="sxs-lookup"><span data-stu-id="d1768-130">Int16</span></span>         | <span data-ttu-id="d1768-131">Automaticky se prodlužuje na 32bitový.</span><span class="sxs-lookup"><span data-stu-id="d1768-131">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="d1768-132">`iUSHORT`(97)</span><span class="sxs-lookup"><span data-stu-id="d1768-132">`iUSHORT` (97)</span></span>           | <span data-ttu-id="d1768-133">UInt16</span><span class="sxs-lookup"><span data-stu-id="d1768-133">UInt16</span></span>        | <span data-ttu-id="d1768-134">Automaticky se prodlužuje na 32bitový.</span><span class="sxs-lookup"><span data-stu-id="d1768-134">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="d1768-135">`iLONG`(98)</span><span class="sxs-lookup"><span data-stu-id="d1768-135">`iLONG` (98)</span></span>             | <span data-ttu-id="d1768-136">Int32</span><span class="sxs-lookup"><span data-stu-id="d1768-136">Int32</span></span>         |                                        |
| <span data-ttu-id="d1768-137">`iULONG`(99)</span><span class="sxs-lookup"><span data-stu-id="d1768-137">`iULONG` (99)</span></span>            | <span data-ttu-id="d1768-138">UInt32</span><span class="sxs-lookup"><span data-stu-id="d1768-138">UInt32</span></span>        |                                        |
| <span data-ttu-id="d1768-139">`iBYTE`(100)</span><span class="sxs-lookup"><span data-stu-id="d1768-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="d1768-140">Byte</span><span class="sxs-lookup"><span data-stu-id="d1768-140">Byte</span></span>          | <span data-ttu-id="d1768-141">Automaticky se prodlužuje na 32bitový.</span><span class="sxs-lookup"><span data-stu-id="d1768-141">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="d1768-142">`iSTRING`(101)</span><span class="sxs-lookup"><span data-stu-id="d1768-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="d1768-143">Index haldy řetězce</span><span class="sxs-lookup"><span data-stu-id="d1768-143">String heap index</span></span> | <span data-ttu-id="d1768-144">*pVal* je index do haldy String.</span><span class="sxs-lookup"><span data-stu-id="d1768-144">*pVal* is an index into the String heap.</span></span> <span data-ttu-id="d1768-145">Pomocí [hodnot IMetadataTables::GetString](imetadatatables-getstring-method.md) získáte skutečnou hodnotu řetězce sloupce.</span><span class="sxs-lookup"><span data-stu-id="d1768-145">Use [IMetadataTables::GetString](imetadatatables-getstring-method.md) to get the actual column String value.</span></span> |
| <span data-ttu-id="d1768-146">`iGUID`(102)</span><span class="sxs-lookup"><span data-stu-id="d1768-146">`iGUID` (102)</span></span>            | <span data-ttu-id="d1768-147">Index haldy Guid</span><span class="sxs-lookup"><span data-stu-id="d1768-147">Guid heap index</span></span> | <span data-ttu-id="d1768-148">*pVal* je index do haldy Guid.</span><span class="sxs-lookup"><span data-stu-id="d1768-148">*pVal* is an index into the Guid heap.</span></span> <span data-ttu-id="d1768-149">Pomocí [iMetadataTables::GetGuid](imetadatatables-getguid-method.md) získat skutečnou hodnotu sloupce Guid.</span><span class="sxs-lookup"><span data-stu-id="d1768-149">Use [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) to get the actual column Guid value.</span></span> |
| <span data-ttu-id="d1768-150">`iBLOB`(103)</span><span class="sxs-lookup"><span data-stu-id="d1768-150">`iBLOB` (103)</span></span>            | <span data-ttu-id="d1768-151">Index haldy objektu blob</span><span class="sxs-lookup"><span data-stu-id="d1768-151">Blob heap index</span></span> | <span data-ttu-id="d1768-152">*pVal* je index do haldy objektu blob.</span><span class="sxs-lookup"><span data-stu-id="d1768-152">*pVal* is an index into the Blob heap.</span></span> <span data-ttu-id="d1768-153">Pomocí [tabulky MetadataTables::GetBlob](imetadatatables-getblob-method.md) získáte skutečnou hodnotu objektu blob sloupce.</span><span class="sxs-lookup"><span data-stu-id="d1768-153">Use [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) to get the actual column Blob value.</span></span> |
  
## <a name="requirements"></a><span data-ttu-id="d1768-154">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d1768-154">Requirements</span></span>  
 <span data-ttu-id="d1768-155">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1768-155">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1768-156">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="d1768-156">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d1768-157">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d1768-157">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d1768-158">**Verze rozhraní .NET Framework**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1768-158">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1768-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1768-159">See also</span></span>

- [<span data-ttu-id="d1768-160">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1768-160">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="d1768-161">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1768-161">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
