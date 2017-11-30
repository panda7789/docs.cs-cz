---
title: "IMetaDataTables::GetTableInfo – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetTableInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetTableInfo
helpviewer_keywords:
- IMetaDataTables::GetTableInfo method [.NET Framework metadata]
- GetTableInfo method [.NET Framework metadata]
ms.assetid: 50cbe557-2322-41aa-8e0d-f967602eaa0f
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0f4ccd9bbd1c7caa9bbeb548176d834dc8844213
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgettableinfo-method"></a><span data-ttu-id="e1f1e-102">IMetaDataTables::GetTableInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="e1f1e-102">IMetaDataTables::GetTableInfo Method</span></span>
<span data-ttu-id="e1f1e-103">Získá název, velikost řádku, počet řádků, počet sloupců a index klíče sloupců zadané tabulky.</span><span class="sxs-lookup"><span data-stu-id="e1f1e-103">Gets the name, row size, number of rows, number of columns, and key column index of the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1f1e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1f1e-104">Syntax</span></span>  
  
```  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1f1e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1f1e-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="e1f1e-106">[v] Identifikátor tabulky, jehož vlastnosti chcete vrátit.</span><span class="sxs-lookup"><span data-stu-id="e1f1e-106">[in] The identifier of the table whose properties to return.</span></span>  
  
 `pcbRow`  
 <span data-ttu-id="e1f1e-107">[out] Ukazatel na velikost v bajtech řádku tabulky.</span><span class="sxs-lookup"><span data-stu-id="e1f1e-107">[out] A pointer to the size, in bytes, of a table row.</span></span>  
  
 `pcRows`  
 <span data-ttu-id="e1f1e-108">[out] Ukazatel na počet řádků v tabulce.</span><span class="sxs-lookup"><span data-stu-id="e1f1e-108">[out] A pointer to the number of rows in the table.</span></span>  
  
 `pcCols`  
 <span data-ttu-id="e1f1e-109">[out] Ukazatel na počet sloupců v tabulce.</span><span class="sxs-lookup"><span data-stu-id="e1f1e-109">[out] A pointer to the number of columns in the table.</span></span>  
  
 `piKey`  
 <span data-ttu-id="e1f1e-110">[out] Ukazatel na index klíče sloupce nebo -1, pokud tabulka nemá žádný klíčový sloupec.</span><span class="sxs-lookup"><span data-stu-id="e1f1e-110">[out] A pointer to the index of the key column, or -1 if the table has no key column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="e1f1e-111">[out] Ukazatel na ukazatel na název tabulky.</span><span class="sxs-lookup"><span data-stu-id="e1f1e-111">[out] A pointer to a pointer to the table name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1f1e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e1f1e-112">Requirements</span></span>  
 <span data-ttu-id="e1f1e-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1f1e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1f1e-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e1f1e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e1f1e-115">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e1f1e-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e1f1e-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1f1e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1f1e-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1f1e-117">See Also</span></span>  
 [<span data-ttu-id="e1f1e-118">Imetadatatables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e1f1e-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="e1f1e-119">Imetadatatables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e1f1e-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
