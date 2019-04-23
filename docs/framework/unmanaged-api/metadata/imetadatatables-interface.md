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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b2298e2d67e8a50e11d53d864f0e78f3b549e45
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59131414"
---
# <a name="imetadatatables-interface"></a><span data-ttu-id="9d234-102">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d234-102">IMetaDataTables Interface</span></span>
<span data-ttu-id="9d234-103">Poskytuje metody pro ukládání a načítání informací o metadatech v tabulkách.</span><span class="sxs-lookup"><span data-stu-id="9d234-103">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9d234-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9d234-104">Methods</span></span>  
  
|<span data-ttu-id="9d234-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9d234-105">Method</span></span>|<span data-ttu-id="9d234-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9d234-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9d234-107">GetBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="9d234-107">GetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|<span data-ttu-id="9d234-108">Získá ukazatel na binární rozsáhlý objekt (BLOB) na zadaný sloupec indexu.</span><span class="sxs-lookup"><span data-stu-id="9d234-108">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>|  
|[<span data-ttu-id="9d234-109">GetBlobHeapSize – metoda</span><span class="sxs-lookup"><span data-stu-id="9d234-109">GetBlobHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|<span data-ttu-id="9d234-110">Získá velikost v bajtech binárního rozsáhlého objektu haldy.</span><span class="sxs-lookup"><span data-stu-id="9d234-110">Gets the size, in bytes, of the BLOB heap.</span></span>|  
|[<span data-ttu-id="9d234-111">GetCodedTokenInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="9d234-111">GetCodedTokenInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|<span data-ttu-id="9d234-112">Získá ukazatel na pole tokenů přidružený index zadaný řádek.</span><span class="sxs-lookup"><span data-stu-id="9d234-112">Gets a pointer to an array of tokens associated with the specified row index.</span></span>|  
|[<span data-ttu-id="9d234-113">GetColumn – metoda</span><span class="sxs-lookup"><span data-stu-id="9d234-113">GetColumn Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|<span data-ttu-id="9d234-114">Získá ukazatel na hodnoty obsažené v sloupci indexu zadaný sloupec v tabulce indexu zadané tabulky.</span><span class="sxs-lookup"><span data-stu-id="9d234-114">Gets a pointer to the values contained in the column at the specified column index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="9d234-115">GetColumnInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="9d234-115">GetColumnInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|<span data-ttu-id="9d234-116">Získá data o zadaný sloupec zadané tabulky.</span><span class="sxs-lookup"><span data-stu-id="9d234-116">Gets data about the specified column in the specified table.</span></span>|  
|[<span data-ttu-id="9d234-117">GetGuid – metoda</span><span class="sxs-lookup"><span data-stu-id="9d234-117">GetGuid Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|<span data-ttu-id="9d234-118">Získá identifikátor GUID z řádku v zadaném indexu.</span><span class="sxs-lookup"><span data-stu-id="9d234-118">Gets a GUID from the row at the specified index.</span></span>|  
|[<span data-ttu-id="9d234-119">GetGuidHeapSize – metoda</span><span class="sxs-lookup"><span data-stu-id="9d234-119">GetGuidHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|<span data-ttu-id="9d234-120">Získá velikost v bajtech haldy GUID.</span><span class="sxs-lookup"><span data-stu-id="9d234-120">Gets the size, in bytes, of the GUID heap.</span></span>|  
|[<span data-ttu-id="9d234-121">GetNextBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="9d234-121">GetNextBlob Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|<span data-ttu-id="9d234-122">Získá index další objektů BLOB v tabulce.</span><span class="sxs-lookup"><span data-stu-id="9d234-122">Gets the index of the next BLOB in the table.</span></span>|  
|[<span data-ttu-id="9d234-123">GetNextGuid – metoda</span><span class="sxs-lookup"><span data-stu-id="9d234-123">GetNextGuid Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|<span data-ttu-id="9d234-124">Získá index další hodnota identifikátoru GUID v aktuálním sloupci tabulky.</span><span class="sxs-lookup"><span data-stu-id="9d234-124">Gets the index of the next GUID value in the current table column.</span></span>|  
|[<span data-ttu-id="9d234-125">GetNextString – metoda</span><span class="sxs-lookup"><span data-stu-id="9d234-125">GetNextString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|<span data-ttu-id="9d234-126">Získá index další řetězce v aktuálním sloupci tabulky.</span><span class="sxs-lookup"><span data-stu-id="9d234-126">Gets the index of the next string in the current table column.</span></span>|  
|[<span data-ttu-id="9d234-127">GetNextUserString – metoda</span><span class="sxs-lookup"><span data-stu-id="9d234-127">GetNextUserString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|<span data-ttu-id="9d234-128">Získá index řádku, který obsahuje další pevně zakódované řetězce v aktuálním sloupci tabulky.</span><span class="sxs-lookup"><span data-stu-id="9d234-128">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>|  
|[<span data-ttu-id="9d234-129">GetNumTables – metoda</span><span class="sxs-lookup"><span data-stu-id="9d234-129">GetNumTables Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|<span data-ttu-id="9d234-130">Získá počet tabulek v rámci aktuálního `IMetaDataTables` instance.</span><span class="sxs-lookup"><span data-stu-id="9d234-130">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>|  
|[<span data-ttu-id="9d234-131">GetRow – metoda</span><span class="sxs-lookup"><span data-stu-id="9d234-131">GetRow Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|<span data-ttu-id="9d234-132">Získá řádek indexu zadaný řádek v tabulce indexu zadané tabulky.</span><span class="sxs-lookup"><span data-stu-id="9d234-132">Gets the row at the specified row index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="9d234-133">GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="9d234-133">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|<span data-ttu-id="9d234-134">Získá řetězec v zadaném indexu ze sloupce tabulky v aktuálním oboru odkaz.</span><span class="sxs-lookup"><span data-stu-id="9d234-134">Gets the string at the specified index from the table column in the current reference scope.</span></span>|  
|[<span data-ttu-id="9d234-135">GetStringHeapSize – metoda</span><span class="sxs-lookup"><span data-stu-id="9d234-135">GetStringHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|<span data-ttu-id="9d234-136">Získá velikost v bajtech, řetězec haldy.</span><span class="sxs-lookup"><span data-stu-id="9d234-136">Gets the size, in bytes, of the string heap.</span></span>|  
|[<span data-ttu-id="9d234-137">GetTableIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="9d234-137">GetTableIndex Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|<span data-ttu-id="9d234-138">Získá index pro tabulku odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="9d234-138">Gets the index for the table referenced by the specified token.</span></span>|  
|[<span data-ttu-id="9d234-139">GetTableInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="9d234-139">GetTableInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|<span data-ttu-id="9d234-140">Získá název, velikost řádku, počet řádků, počet sloupců a index sloupce klíče tabulky indexu zadané tabulky.</span><span class="sxs-lookup"><span data-stu-id="9d234-140">Gets the name, row size, number of rows, number of columns, and key column index of the table at the specified table index.</span></span>|  
|[<span data-ttu-id="9d234-141">GetUserString – metoda</span><span class="sxs-lookup"><span data-stu-id="9d234-141">GetUserString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|<span data-ttu-id="9d234-142">Získá řetězec pevně zakódované v zadaném indexu ve sloupci řetězce v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="9d234-142">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>|  
|[<span data-ttu-id="9d234-143">GetUserStringHeapSize – metoda</span><span class="sxs-lookup"><span data-stu-id="9d234-143">GetUserStringHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|<span data-ttu-id="9d234-144">Získá velikost v bajtech, řetězec haldy uživatele.</span><span class="sxs-lookup"><span data-stu-id="9d234-144">Gets the size, in bytes, of the user string heap.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9d234-145">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d234-145">Requirements</span></span>  
 <span data-ttu-id="9d234-146">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d234-146">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d234-147">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9d234-147">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9d234-148">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9d234-148">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9d234-149">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d234-149">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d234-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d234-150">See also</span></span>

- [<span data-ttu-id="9d234-151">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="9d234-151">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="9d234-152">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d234-152">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
