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
ms.openlocfilehash: 376b9ff09ad38ca43d57fcf064458e0331da8aad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441995"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="5cc65-102">IMetaDataTables::GetColumn – metoda</span><span class="sxs-lookup"><span data-stu-id="5cc65-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="5cc65-103">Získá ukazatel na hodnotu obsaženou v buňce zadaného sloupce a řádku v dané tabulce.</span><span class="sxs-lookup"><span data-stu-id="5cc65-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cc65-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5cc65-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cc65-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5cc65-105">Parameters</span></span>

 `ixTbl`  
 <span data-ttu-id="5cc65-106">pro Index tabulky</span><span class="sxs-lookup"><span data-stu-id="5cc65-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="5cc65-107">pro Index sloupce v tabulce</span><span class="sxs-lookup"><span data-stu-id="5cc65-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="5cc65-108">pro Index řádku v tabulce</span><span class="sxs-lookup"><span data-stu-id="5cc65-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="5cc65-109">mimo Ukazatel na hodnotu v buňce.</span><span class="sxs-lookup"><span data-stu-id="5cc65-109">[out] A pointer to the value in the cell.</span></span>  
 
## <a name="remarks"></a><span data-ttu-id="5cc65-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5cc65-110">Remarks</span></span>

<span data-ttu-id="5cc65-111">Interpretace hodnoty vrácené prostřednictvím `pVal` závisí na typu sloupce.</span><span class="sxs-lookup"><span data-stu-id="5cc65-111">The interpretion of the value returned through `pVal` depends on the column's type.</span></span> <span data-ttu-id="5cc65-112">Typ sloupce lze určit voláním [IMetaDataTables. GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="5cc65-112">The column type can be determined by calling [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span></span>

- <span data-ttu-id="5cc65-113">Metoda **GetColumn** automaticky převede sloupce typu **RID** nebo **CodedToken** na úplné hodnoty 32 `mdToken`.</span><span class="sxs-lookup"><span data-stu-id="5cc65-113">The **GetColumn** method automatically converts columns of type **Rid** or **CodedToken** to full 32-bit `mdToken` values.</span></span>
- <span data-ttu-id="5cc65-114">Také automaticky převádí 8bitové nebo 16bitové hodnoty na hodnoty Full 32-bit.</span><span class="sxs-lookup"><span data-stu-id="5cc65-114">It also automatically converts 8-bit or 16-bit values to full 32-bit values.</span></span> 
- <span data-ttu-id="5cc65-115">Pro sloupce typu *haldy* bude vrácená *Pval* index do odpovídající haldy.</span><span class="sxs-lookup"><span data-stu-id="5cc65-115">For *heap* type columns, the returned *pVal* will be an index into the corresponding heap.</span></span>

| <span data-ttu-id="5cc65-116">Typ sloupce</span><span class="sxs-lookup"><span data-stu-id="5cc65-116">Column type</span></span>              | <span data-ttu-id="5cc65-117">pVal obsahuje</span><span class="sxs-lookup"><span data-stu-id="5cc65-117">pVal contains</span></span> | <span data-ttu-id="5cc65-118">Komentář</span><span class="sxs-lookup"><span data-stu-id="5cc65-118">Comment</span></span>                          |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="5cc65-119">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="5cc65-119">`0`..`iRidMax`</span></span><br><span data-ttu-id="5cc65-120">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="5cc65-120">(0..63)</span></span>  | <span data-ttu-id="5cc65-121">mdToken</span><span class="sxs-lookup"><span data-stu-id="5cc65-121">mdToken</span></span>     | <span data-ttu-id="5cc65-122">*Pval* bude obsahovat úplný token.</span><span class="sxs-lookup"><span data-stu-id="5cc65-122">*pVal* will contain a full Token.</span></span> <span data-ttu-id="5cc65-123">Funkce automaticky převede identifikátor RID na úplný token.</span><span class="sxs-lookup"><span data-stu-id="5cc65-123">The function automatically converts the Rid into a full token.</span></span> |
| <span data-ttu-id="5cc65-124">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="5cc65-124">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="5cc65-125">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="5cc65-125">(64..95)</span></span> | <span data-ttu-id="5cc65-126">mdToken</span><span class="sxs-lookup"><span data-stu-id="5cc65-126">mdToken</span></span> | <span data-ttu-id="5cc65-127">Po návratu bude *Pval* obsahovat úplný token.</span><span class="sxs-lookup"><span data-stu-id="5cc65-127">Upon return, *pVal* will contain a full Token.</span></span> <span data-ttu-id="5cc65-128">Funkce automaticky dekomprimuje CodedToken na úplný token.</span><span class="sxs-lookup"><span data-stu-id="5cc65-128">The function automatically decompresses the CodedToken into a full token.</span></span> |
| <span data-ttu-id="5cc65-129">`iSHORT` (96)</span><span class="sxs-lookup"><span data-stu-id="5cc65-129">`iSHORT` (96)</span></span>            | <span data-ttu-id="5cc65-130">Int16</span><span class="sxs-lookup"><span data-stu-id="5cc65-130">Int16</span></span>         | <span data-ttu-id="5cc65-131">Automaticky přihlašovat-rozšířené na 32-bit.</span><span class="sxs-lookup"><span data-stu-id="5cc65-131">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="5cc65-132">`iUSHORT` (97)</span><span class="sxs-lookup"><span data-stu-id="5cc65-132">`iUSHORT` (97)</span></span>           | <span data-ttu-id="5cc65-133">UInt16</span><span class="sxs-lookup"><span data-stu-id="5cc65-133">UInt16</span></span>        | <span data-ttu-id="5cc65-134">Automaticky přihlašovat-rozšířené na 32-bit.</span><span class="sxs-lookup"><span data-stu-id="5cc65-134">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="5cc65-135">`iLONG` (98)</span><span class="sxs-lookup"><span data-stu-id="5cc65-135">`iLONG` (98)</span></span>             | <span data-ttu-id="5cc65-136">Datový typ Int32</span><span class="sxs-lookup"><span data-stu-id="5cc65-136">Int32</span></span>         |                                        | 
| <span data-ttu-id="5cc65-137">`iULONG` (99)</span><span class="sxs-lookup"><span data-stu-id="5cc65-137">`iULONG` (99)</span></span>            | <span data-ttu-id="5cc65-138">UInt32</span><span class="sxs-lookup"><span data-stu-id="5cc65-138">UInt32</span></span>        |                                        |
| <span data-ttu-id="5cc65-139">`iBYTE` (100)</span><span class="sxs-lookup"><span data-stu-id="5cc65-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="5cc65-140">Byte</span><span class="sxs-lookup"><span data-stu-id="5cc65-140">Byte</span></span>          | <span data-ttu-id="5cc65-141">Automaticky přihlašovat-rozšířené na 32-bit.</span><span class="sxs-lookup"><span data-stu-id="5cc65-141">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="5cc65-142">`iSTRING` (101)</span><span class="sxs-lookup"><span data-stu-id="5cc65-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="5cc65-143">Index haldy řetězců</span><span class="sxs-lookup"><span data-stu-id="5cc65-143">String heap index</span></span> | <span data-ttu-id="5cc65-144">*Pval* je index haldy řetězců.</span><span class="sxs-lookup"><span data-stu-id="5cc65-144">*pVal* is an index into the String heap.</span></span> <span data-ttu-id="5cc65-145">K získání skutečné hodnoty řetězce sloupce použijte [IMetadataTables:: GetString](imetadatatables-getstring-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5cc65-145">Use [IMetadataTables::GetString](imetadatatables-getstring-method.md) to get the actual column String value.</span></span> |
| <span data-ttu-id="5cc65-146">`iGUID` (102)</span><span class="sxs-lookup"><span data-stu-id="5cc65-146">`iGUID` (102)</span></span>            | <span data-ttu-id="5cc65-147">Index haldy GUID</span><span class="sxs-lookup"><span data-stu-id="5cc65-147">Guid heap index</span></span> | <span data-ttu-id="5cc65-148">*Pval* je index haldy identifikátoru GUID.</span><span class="sxs-lookup"><span data-stu-id="5cc65-148">*pVal* is an index into the Guid heap.</span></span> <span data-ttu-id="5cc65-149">K získání skutečné hodnoty GUID sloupce použijte [IMetadataTables:: GetGUID](imetadatatables-getguid-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5cc65-149">Use [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) to get the actual column Guid value.</span></span> |
| <span data-ttu-id="5cc65-150">`iBLOB` (103)</span><span class="sxs-lookup"><span data-stu-id="5cc65-150">`iBLOB` (103)</span></span>            | <span data-ttu-id="5cc65-151">Index haldy objektů BLOB</span><span class="sxs-lookup"><span data-stu-id="5cc65-151">Blob heap index</span></span> | <span data-ttu-id="5cc65-152">*Pval* je index haldy objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="5cc65-152">*pVal* is an index into the Blob heap.</span></span> <span data-ttu-id="5cc65-153">K získání skutečné hodnoty objektu BLOB sloupce použijte [IMetadataTables:: getblob](imetadatatables-getblob-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5cc65-153">Use [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) to get the actual column Blob value.</span></span> |
  
## <a name="requirements"></a><span data-ttu-id="5cc65-154">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5cc65-154">Requirements</span></span>  
 <span data-ttu-id="5cc65-155">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cc65-155">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cc65-156">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5cc65-156">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5cc65-157">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="5cc65-157">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5cc65-158">**Verze .NET Framework** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cc65-158">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cc65-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5cc65-159">See also</span></span>

- [<span data-ttu-id="5cc65-160">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5cc65-160">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="5cc65-161">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5cc65-161">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
