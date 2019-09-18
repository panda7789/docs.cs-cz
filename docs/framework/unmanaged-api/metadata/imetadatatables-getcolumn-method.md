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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 853f137d91e1b3eb4f3f65a06522618f8441dcb3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053680"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="4d433-102">IMetaDataTables::GetColumn – metoda</span><span class="sxs-lookup"><span data-stu-id="4d433-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="4d433-103">Získá ukazatel na hodnotu obsaženou v buňce zadaného sloupce a řádku v dané tabulce.</span><span class="sxs-lookup"><span data-stu-id="4d433-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d433-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d433-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d433-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d433-105">Parameters</span></span>

 `ixTbl`  
 <span data-ttu-id="4d433-106">pro Index tabulky</span><span class="sxs-lookup"><span data-stu-id="4d433-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="4d433-107">pro Index sloupce v tabulce</span><span class="sxs-lookup"><span data-stu-id="4d433-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="4d433-108">pro Index řádku v tabulce</span><span class="sxs-lookup"><span data-stu-id="4d433-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="4d433-109">mimo Ukazatel na hodnotu v buňce.</span><span class="sxs-lookup"><span data-stu-id="4d433-109">[out] A pointer to the value in the cell.</span></span>  
 
## <a name="remarks"></a><span data-ttu-id="4d433-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d433-110">Remarks</span></span>

<span data-ttu-id="4d433-111">Interpretace hodnoty vrácené prostřednictvím `pVal` závisí na typu sloupce.</span><span class="sxs-lookup"><span data-stu-id="4d433-111">The interpretion of the value returned through `pVal` depends on the column's type.</span></span> <span data-ttu-id="4d433-112">Typ sloupce lze určit voláním [IMetaDataTables. GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="4d433-112">The column type can be determined by calling [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span></span>

- <span data-ttu-id="4d433-113">Metoda **GetColumn** automaticky převede sloupce typu **RID** nebo **CodedToken** `mdToken` na úplné 32 hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4d433-113">The **GetColumn** method automatically converts columns of type **Rid** or **CodedToken** to full 32-bit `mdToken` values.</span></span>
- <span data-ttu-id="4d433-114">Také automaticky převádí 8bitové nebo 16bitové hodnoty na hodnoty Full 32-bit.</span><span class="sxs-lookup"><span data-stu-id="4d433-114">It also automatically converts 8-bit or 16-bit values to full 32-bit values.</span></span> 
- <span data-ttu-id="4d433-115">Pro sloupce typu *haldy* bude vrácená *Pval* index do odpovídající haldy.</span><span class="sxs-lookup"><span data-stu-id="4d433-115">For *heap* type columns, the returned *pVal* will be an index into the corresponding heap.</span></span>

| <span data-ttu-id="4d433-116">Typ sloupce</span><span class="sxs-lookup"><span data-stu-id="4d433-116">Column type</span></span>              | <span data-ttu-id="4d433-117">pVal obsahuje</span><span class="sxs-lookup"><span data-stu-id="4d433-117">pVal contains</span></span> | <span data-ttu-id="4d433-118">Komentář</span><span class="sxs-lookup"><span data-stu-id="4d433-118">Comment</span></span>                          |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="4d433-119">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="4d433-119">`0`..`iRidMax`</span></span><br><span data-ttu-id="4d433-120">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="4d433-120">(0..63)</span></span>  | <span data-ttu-id="4d433-121">mdToken</span><span class="sxs-lookup"><span data-stu-id="4d433-121">mdToken</span></span>     | <span data-ttu-id="4d433-122">*Pval* bude obsahovat úplný token.</span><span class="sxs-lookup"><span data-stu-id="4d433-122">*pVal* will contain a full Token.</span></span> <span data-ttu-id="4d433-123">Funkce automaticky převede identifikátor RID na úplný token.</span><span class="sxs-lookup"><span data-stu-id="4d433-123">The function automatically converts the Rid into a full token.</span></span> |
| <span data-ttu-id="4d433-124">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="4d433-124">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="4d433-125">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="4d433-125">(64..95)</span></span> | <span data-ttu-id="4d433-126">mdToken</span><span class="sxs-lookup"><span data-stu-id="4d433-126">mdToken</span></span> | <span data-ttu-id="4d433-127">Po návratu bude *Pval* obsahovat úplný token.</span><span class="sxs-lookup"><span data-stu-id="4d433-127">Upon return, *pVal* will contain a full Token.</span></span> <span data-ttu-id="4d433-128">Funkce automaticky dekomprimuje CodedToken na úplný token.</span><span class="sxs-lookup"><span data-stu-id="4d433-128">The function automatically decompresses the CodedToken into a full token.</span></span> |
| <span data-ttu-id="4d433-129">`iSHORT`(96)</span><span class="sxs-lookup"><span data-stu-id="4d433-129">`iSHORT` (96)</span></span>            | <span data-ttu-id="4d433-130">Int16</span><span class="sxs-lookup"><span data-stu-id="4d433-130">Int16</span></span>         | <span data-ttu-id="4d433-131">Automaticky přihlašovat-rozšířené na 32-bit.</span><span class="sxs-lookup"><span data-stu-id="4d433-131">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="4d433-132">`iUSHORT`(97)</span><span class="sxs-lookup"><span data-stu-id="4d433-132">`iUSHORT` (97)</span></span>           | <span data-ttu-id="4d433-133">UInt16</span><span class="sxs-lookup"><span data-stu-id="4d433-133">UInt16</span></span>        | <span data-ttu-id="4d433-134">Automaticky přihlašovat-rozšířené na 32-bit.</span><span class="sxs-lookup"><span data-stu-id="4d433-134">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="4d433-135">`iLONG`(98)</span><span class="sxs-lookup"><span data-stu-id="4d433-135">`iLONG` (98)</span></span>             | <span data-ttu-id="4d433-136">Int32</span><span class="sxs-lookup"><span data-stu-id="4d433-136">Int32</span></span>         |                                        | 
| <span data-ttu-id="4d433-137">`iULONG`(99)</span><span class="sxs-lookup"><span data-stu-id="4d433-137">`iULONG` (99)</span></span>            | <span data-ttu-id="4d433-138">UInt32</span><span class="sxs-lookup"><span data-stu-id="4d433-138">UInt32</span></span>        |                                        |
| <span data-ttu-id="4d433-139">`iBYTE`(100)</span><span class="sxs-lookup"><span data-stu-id="4d433-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="4d433-140">Byte</span><span class="sxs-lookup"><span data-stu-id="4d433-140">Byte</span></span>          | <span data-ttu-id="4d433-141">Automaticky přihlašovat-rozšířené na 32-bit.</span><span class="sxs-lookup"><span data-stu-id="4d433-141">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="4d433-142">`iSTRING`(101)</span><span class="sxs-lookup"><span data-stu-id="4d433-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="4d433-143">Index haldy řetězců</span><span class="sxs-lookup"><span data-stu-id="4d433-143">String heap index</span></span> | <span data-ttu-id="4d433-144">*Pval* je index haldy řetězců.</span><span class="sxs-lookup"><span data-stu-id="4d433-144">*pVal* is an index into the String heap.</span></span> <span data-ttu-id="4d433-145">K získání skutečné hodnoty řetězce sloupce použijte [IMetadataTables:: GetString](imetadatatables-getstring-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4d433-145">Use [IMetadataTables::GetString](imetadatatables-getstring-method.md) to get the actual column String value.</span></span> |
| <span data-ttu-id="4d433-146">`iGUID`(102)</span><span class="sxs-lookup"><span data-stu-id="4d433-146">`iGUID` (102)</span></span>            | <span data-ttu-id="4d433-147">Index haldy GUID</span><span class="sxs-lookup"><span data-stu-id="4d433-147">Guid heap index</span></span> | <span data-ttu-id="4d433-148">*Pval* je index haldy identifikátoru GUID.</span><span class="sxs-lookup"><span data-stu-id="4d433-148">*pVal* is an index into the Guid heap.</span></span> <span data-ttu-id="4d433-149">K získání skutečné hodnoty GUID sloupce použijte [IMetadataTables:: GetGUID](imetadatatables-getguid-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4d433-149">Use [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) to get the actual column Guid value.</span></span> |
| <span data-ttu-id="4d433-150">`iBLOB`(103)</span><span class="sxs-lookup"><span data-stu-id="4d433-150">`iBLOB` (103)</span></span>            | <span data-ttu-id="4d433-151">Index haldy objektů BLOB</span><span class="sxs-lookup"><span data-stu-id="4d433-151">Blob heap index</span></span> | <span data-ttu-id="4d433-152">*Pval* je index haldy objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="4d433-152">*pVal* is an index into the Blob heap.</span></span> <span data-ttu-id="4d433-153">K získání skutečné hodnoty objektu BLOB sloupce použijte [IMetadataTables:: getblob](imetadatatables-getblob-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4d433-153">Use [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) to get the actual column Blob value.</span></span> |
  
## <a name="requirements"></a><span data-ttu-id="4d433-154">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d433-154">Requirements</span></span>  
 <span data-ttu-id="4d433-155">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d433-155">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d433-156">**Hlaviček** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4d433-156">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4d433-157">**Knihovna** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="4d433-157">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4d433-158">**Verze .NET Framework**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d433-158">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d433-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d433-159">See also</span></span>

- [<span data-ttu-id="4d433-160">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d433-160">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="4d433-161">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d433-161">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
