---
title: "IMetaDataTables – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables
helpviewer_keywords: IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c89d615fbeeff4a60eb386d58c573ee7905f538d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatables-interface"></a><span data-ttu-id="03107-102">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="03107-102">IMetaDataTables Interface</span></span>
<span data-ttu-id="03107-103">Poskytuje metody pro ukládání a načítání informací metadat v tabulkách.</span><span class="sxs-lookup"><span data-stu-id="03107-103">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="03107-104">Metody</span><span class="sxs-lookup"><span data-stu-id="03107-104">Methods</span></span>  
  
|<span data-ttu-id="03107-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="03107-105">Method</span></span>|<span data-ttu-id="03107-106">Popis</span><span class="sxs-lookup"><span data-stu-id="03107-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="03107-107">Getblob – metoda</span><span class="sxs-lookup"><span data-stu-id="03107-107">GetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|<span data-ttu-id="03107-108">Získá ukazatel na binární rozsáhlý objekt (binární rozsáhlý OBJEKT) v indexu zadaný sloupec.</span><span class="sxs-lookup"><span data-stu-id="03107-108">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>|  
|[<span data-ttu-id="03107-109">Getblobheapsize – metoda</span><span class="sxs-lookup"><span data-stu-id="03107-109">GetBlobHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|<span data-ttu-id="03107-110">Získá velikost v bajtech haldě objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="03107-110">Gets the size, in bytes, of the BLOB heap.</span></span>|  
|[<span data-ttu-id="03107-111">Getcodedtokeninfo – metoda</span><span class="sxs-lookup"><span data-stu-id="03107-111">GetCodedTokenInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|<span data-ttu-id="03107-112">Získá ukazatel na pole tokeny přidružený index zadaný řádku.</span><span class="sxs-lookup"><span data-stu-id="03107-112">Gets a pointer to an array of tokens associated with the specified row index.</span></span>|  
|[<span data-ttu-id="03107-113">GetColumn – metoda</span><span class="sxs-lookup"><span data-stu-id="03107-113">GetColumn Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|<span data-ttu-id="03107-114">Získá ukazatel na hodnoty obsažené v sloupce v indexu zadaný sloupec, v tabulce u zadané tabulky indexu.</span><span class="sxs-lookup"><span data-stu-id="03107-114">Gets a pointer to the values contained in the column at the specified column index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="03107-115">GetColumnInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="03107-115">GetColumnInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|<span data-ttu-id="03107-116">Získá data o zadaný sloupec zadané tabulky.</span><span class="sxs-lookup"><span data-stu-id="03107-116">Gets data about the specified column in the specified table.</span></span>|  
|[<span data-ttu-id="03107-117">Getguid – metoda</span><span class="sxs-lookup"><span data-stu-id="03107-117">GetGuid Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|<span data-ttu-id="03107-118">Získá identifikátor GUID z řádek na pozici se zadaným indexem.</span><span class="sxs-lookup"><span data-stu-id="03107-118">Gets a GUID from the row at the specified index.</span></span>|  
|[<span data-ttu-id="03107-119">Getguidheapsize – metoda</span><span class="sxs-lookup"><span data-stu-id="03107-119">GetGuidHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|<span data-ttu-id="03107-120">Získá velikost v bajtech haldě identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="03107-120">Gets the size, in bytes, of the GUID heap.</span></span>|  
|[<span data-ttu-id="03107-121">Getnextblob – metoda</span><span class="sxs-lookup"><span data-stu-id="03107-121">GetNextBlob Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|<span data-ttu-id="03107-122">Získá index další objektů BLOB v tabulce.</span><span class="sxs-lookup"><span data-stu-id="03107-122">Gets the index of the next BLOB in the table.</span></span>|  
|[<span data-ttu-id="03107-123">Getnextguid – metoda</span><span class="sxs-lookup"><span data-stu-id="03107-123">GetNextGuid Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|<span data-ttu-id="03107-124">Získá index další hodnota identifikátoru GUID v aktuální sloupec tabulky.</span><span class="sxs-lookup"><span data-stu-id="03107-124">Gets the index of the next GUID value in the current table column.</span></span>|  
|[<span data-ttu-id="03107-125">Getnextstring – metoda</span><span class="sxs-lookup"><span data-stu-id="03107-125">GetNextString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|<span data-ttu-id="03107-126">Získá index další řetězce v aktuálním sloupec tabulky.</span><span class="sxs-lookup"><span data-stu-id="03107-126">Gets the index of the next string in the current table column.</span></span>|  
|[<span data-ttu-id="03107-127">Getnextuserstring – metoda</span><span class="sxs-lookup"><span data-stu-id="03107-127">GetNextUserString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|<span data-ttu-id="03107-128">Získá index řádku, který obsahuje další pevně řetězce v aktuálním sloupec tabulky.</span><span class="sxs-lookup"><span data-stu-id="03107-128">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>|  
|[<span data-ttu-id="03107-129">Getnumtables – metoda</span><span class="sxs-lookup"><span data-stu-id="03107-129">GetNumTables Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|<span data-ttu-id="03107-130">Získá počet tabulek v rozsahu aktuální `IMetaDataTables` instance.</span><span class="sxs-lookup"><span data-stu-id="03107-130">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>|  
|[<span data-ttu-id="03107-131">GetRow – metoda</span><span class="sxs-lookup"><span data-stu-id="03107-131">GetRow Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|<span data-ttu-id="03107-132">Získá řádek indexem zadaný řádek v tabulce u zadané tabulky indexu.</span><span class="sxs-lookup"><span data-stu-id="03107-132">Gets the row at the specified row index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="03107-133">GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="03107-133">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|<span data-ttu-id="03107-134">Získá řetězec v zadaném indexu ze sloupce tabulky v aktuálním oboru odkaz.</span><span class="sxs-lookup"><span data-stu-id="03107-134">Gets the string at the specified index from the table column in the current reference scope.</span></span>|  
|[<span data-ttu-id="03107-135">Getstringheapsize – metoda</span><span class="sxs-lookup"><span data-stu-id="03107-135">GetStringHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|<span data-ttu-id="03107-136">Získá velikost v bajtech haldy řetězce.</span><span class="sxs-lookup"><span data-stu-id="03107-136">Gets the size, in bytes, of the string heap.</span></span>|  
|[<span data-ttu-id="03107-137">Gettableindex – metoda</span><span class="sxs-lookup"><span data-stu-id="03107-137">GetTableIndex Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|<span data-ttu-id="03107-138">Získá index pro tabulku odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="03107-138">Gets the index for the table referenced by the specified token.</span></span>|  
|[<span data-ttu-id="03107-139">Gettableinfo – metoda</span><span class="sxs-lookup"><span data-stu-id="03107-139">GetTableInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|<span data-ttu-id="03107-140">Získá název, velikost řádku, počet řádků, počet sloupců a index sloupce klíče tabulky v indexu zadané tabulky.</span><span class="sxs-lookup"><span data-stu-id="03107-140">Gets the name, row size, number of rows, number of columns, and key column index of the table at the specified table index.</span></span>|  
|[<span data-ttu-id="03107-141">Getuserstring – metoda</span><span class="sxs-lookup"><span data-stu-id="03107-141">GetUserString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|<span data-ttu-id="03107-142">Získá řetězec pevně v zadaném indexu ve sloupci řetězce v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="03107-142">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>|  
|[<span data-ttu-id="03107-143">Getuserstringheapsize – metoda</span><span class="sxs-lookup"><span data-stu-id="03107-143">GetUserStringHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|<span data-ttu-id="03107-144">Získá velikost v bajtech haldě řetězec uživatele.</span><span class="sxs-lookup"><span data-stu-id="03107-144">Gets the size, in bytes, of the user string heap.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="03107-145">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03107-145">Requirements</span></span>  
 <span data-ttu-id="03107-146">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03107-146">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03107-147">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="03107-147">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03107-148">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="03107-148">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="03107-149">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03107-149">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03107-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="03107-150">See Also</span></span>  
 [<span data-ttu-id="03107-151">Rozhraní metadat</span><span class="sxs-lookup"><span data-stu-id="03107-151">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="03107-152">Imetadatatables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="03107-152">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
