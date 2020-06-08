---
title: IMetaDataTables – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables
helpviewer_keywords:
- IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type:
- apiref
ms.openlocfilehash: 2105033e684ec172e24adfb14bcab7668b388af3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501118"
---
# <a name="imetadatatables-interface"></a><span data-ttu-id="d0b33-102">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0b33-102">IMetaDataTables Interface</span></span>
<span data-ttu-id="d0b33-103">Poskytuje metody pro ukládání a načítání informací o metadatech v tabulkách.</span><span class="sxs-lookup"><span data-stu-id="d0b33-103">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0b33-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d0b33-104">Methods</span></span>  
  
|<span data-ttu-id="d0b33-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d0b33-105">Method</span></span>|<span data-ttu-id="d0b33-106">Description</span><span class="sxs-lookup"><span data-stu-id="d0b33-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0b33-107">GetBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="d0b33-107">GetBlob Method</span></span>](imetadatatables-getblob-method.md)|<span data-ttu-id="d0b33-108">Získá ukazatel na binární rozsáhlý objekt (BLOB) v zadaném indexu sloupce.</span><span class="sxs-lookup"><span data-stu-id="d0b33-108">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>|  
|[<span data-ttu-id="d0b33-109">GetBlobHeapSize – metoda</span><span class="sxs-lookup"><span data-stu-id="d0b33-109">GetBlobHeapSize Method</span></span>](imetadatatables-getblobheapsize-method.md)|<span data-ttu-id="d0b33-110">Získá velikost haldy objektů BLOB v bajtech.</span><span class="sxs-lookup"><span data-stu-id="d0b33-110">Gets the size, in bytes, of the BLOB heap.</span></span>|  
|[<span data-ttu-id="d0b33-111">GetCodedTokenInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="d0b33-111">GetCodedTokenInfo Method</span></span>](imetadatatables-getcodedtokeninfo-method.md)|<span data-ttu-id="d0b33-112">Získá ukazatel na pole tokenů přidružené k zadanému indexu řádků.</span><span class="sxs-lookup"><span data-stu-id="d0b33-112">Gets a pointer to an array of tokens associated with the specified row index.</span></span>|  
|[<span data-ttu-id="d0b33-113">GetColumn – metoda</span><span class="sxs-lookup"><span data-stu-id="d0b33-113">GetColumn Method</span></span>](imetadatatables-getcolumn-method.md)|<span data-ttu-id="d0b33-114">Získá ukazatel na hodnoty obsažené ve sloupci v zadaném indexu sloupce v tabulce se zadaným indexem tabulky.</span><span class="sxs-lookup"><span data-stu-id="d0b33-114">Gets a pointer to the values contained in the column at the specified column index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="d0b33-115">GetColumnInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="d0b33-115">GetColumnInfo Method</span></span>](imetadatatables-getcolumninfo-method.md)|<span data-ttu-id="d0b33-116">Načte data o zadaném sloupci v zadané tabulce.</span><span class="sxs-lookup"><span data-stu-id="d0b33-116">Gets data about the specified column in the specified table.</span></span>|  
|[<span data-ttu-id="d0b33-117">GetGuid – metoda</span><span class="sxs-lookup"><span data-stu-id="d0b33-117">GetGuid Method</span></span>](imetadatatables-getguid-method.md)|<span data-ttu-id="d0b33-118">Získá identifikátor GUID z řádku na zadaném indexu.</span><span class="sxs-lookup"><span data-stu-id="d0b33-118">Gets a GUID from the row at the specified index.</span></span>|  
|[<span data-ttu-id="d0b33-119">GetGuidHeapSize – metoda</span><span class="sxs-lookup"><span data-stu-id="d0b33-119">GetGuidHeapSize Method</span></span>](imetadatatables-getguidheapsize-method.md)|<span data-ttu-id="d0b33-120">Získá velikost haldy GUID (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="d0b33-120">Gets the size, in bytes, of the GUID heap.</span></span>|  
|[<span data-ttu-id="d0b33-121">GetNextBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="d0b33-121">GetNextBlob Method</span></span>](imetadatatables-getnextblob-method.md)|<span data-ttu-id="d0b33-122">Získá index dalšího objektu BLOB v tabulce.</span><span class="sxs-lookup"><span data-stu-id="d0b33-122">Gets the index of the next BLOB in the table.</span></span>|  
|[<span data-ttu-id="d0b33-123">GetNextGuid – metoda</span><span class="sxs-lookup"><span data-stu-id="d0b33-123">GetNextGuid Method</span></span>](imetadatatables-getnextguid-method.md)|<span data-ttu-id="d0b33-124">Získá index další hodnoty GUID ve sloupci aktuální tabulky.</span><span class="sxs-lookup"><span data-stu-id="d0b33-124">Gets the index of the next GUID value in the current table column.</span></span>|  
|[<span data-ttu-id="d0b33-125">GetNextString – metoda</span><span class="sxs-lookup"><span data-stu-id="d0b33-125">GetNextString Method</span></span>](imetadatatables-getnextstring-method.md)|<span data-ttu-id="d0b33-126">Získá index dalšího řetězce ve sloupci aktuální tabulky.</span><span class="sxs-lookup"><span data-stu-id="d0b33-126">Gets the index of the next string in the current table column.</span></span>|  
|[<span data-ttu-id="d0b33-127">GetNextUserString – metoda</span><span class="sxs-lookup"><span data-stu-id="d0b33-127">GetNextUserString Method</span></span>](imetadatatables-getnextuserstring-method.md)|<span data-ttu-id="d0b33-128">Získá index řádku, který obsahuje další pevně zakódovaný řetězec ve sloupci aktuální tabulky.</span><span class="sxs-lookup"><span data-stu-id="d0b33-128">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>|  
|[<span data-ttu-id="d0b33-129">GetNumTables – metoda</span><span class="sxs-lookup"><span data-stu-id="d0b33-129">GetNumTables Method</span></span>](imetadatatables-getnumtables-method.md)|<span data-ttu-id="d0b33-130">Získá počet tabulek v rozsahu aktuální `IMetaDataTables` instance.</span><span class="sxs-lookup"><span data-stu-id="d0b33-130">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>|  
|[<span data-ttu-id="d0b33-131">GetRow – metoda</span><span class="sxs-lookup"><span data-stu-id="d0b33-131">GetRow Method</span></span>](imetadatatables-getrow-method.md)|<span data-ttu-id="d0b33-132">Získá řádek v zadaném indexu řádku v tabulce se zadaným indexem tabulky.</span><span class="sxs-lookup"><span data-stu-id="d0b33-132">Gets the row at the specified row index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="d0b33-133">GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="d0b33-133">GetString Method</span></span>](imetadatatables-getstring-method.md)|<span data-ttu-id="d0b33-134">Získá řetězec na zadaném indexu ze sloupce tabulky v aktuálním oboru odkazů.</span><span class="sxs-lookup"><span data-stu-id="d0b33-134">Gets the string at the specified index from the table column in the current reference scope.</span></span>|  
|[<span data-ttu-id="d0b33-135">GetStringHeapSize – metoda</span><span class="sxs-lookup"><span data-stu-id="d0b33-135">GetStringHeapSize Method</span></span>](imetadatatables-getstringheapsize-method.md)|<span data-ttu-id="d0b33-136">Získá velikost haldy řetězce v bajtech.</span><span class="sxs-lookup"><span data-stu-id="d0b33-136">Gets the size, in bytes, of the string heap.</span></span>|  
|[<span data-ttu-id="d0b33-137">GetTableIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="d0b33-137">GetTableIndex Method</span></span>](imetadatatables-gettableindex-method.md)|<span data-ttu-id="d0b33-138">Získá index pro tabulku, na kterou odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="d0b33-138">Gets the index for the table referenced by the specified token.</span></span>|  
|[<span data-ttu-id="d0b33-139">GetTableInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="d0b33-139">GetTableInfo Method</span></span>](imetadatatables-gettableinfo-method.md)|<span data-ttu-id="d0b33-140">Získá název, velikost řádku, počet řádků, počet sloupců a klíčový index sloupce tabulky v zadaném indexu tabulky.</span><span class="sxs-lookup"><span data-stu-id="d0b33-140">Gets the name, row size, number of rows, number of columns, and key column index of the table at the specified table index.</span></span>|  
|[<span data-ttu-id="d0b33-141">GetUserString – metoda</span><span class="sxs-lookup"><span data-stu-id="d0b33-141">GetUserString Method</span></span>](imetadatatables-getuserstring-method.md)|<span data-ttu-id="d0b33-142">Získá pevně zakódovaný řetězec na zadaném indexu ve sloupci řetězce v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="d0b33-142">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>|  
|[<span data-ttu-id="d0b33-143">GetUserStringHeapSize – metoda</span><span class="sxs-lookup"><span data-stu-id="d0b33-143">GetUserStringHeapSize Method</span></span>](imetadatatables-getuserstringheapsize-method.md)|<span data-ttu-id="d0b33-144">Získá velikost haldy řetězců uživatele v bajtech.</span><span class="sxs-lookup"><span data-stu-id="d0b33-144">Gets the size, in bytes, of the user string heap.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d0b33-145">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d0b33-145">Requirements</span></span>  
 <span data-ttu-id="d0b33-146">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0b33-146">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0b33-147">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d0b33-147">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d0b33-148">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="d0b33-148">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d0b33-149">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0b33-149">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0b33-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0b33-150">See also</span></span>

- [<span data-ttu-id="d0b33-151">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="d0b33-151">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="d0b33-152">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0b33-152">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
