---
title: IMetaDataTables::GetTableInfo – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableInfo
helpviewer_keywords:
- IMetaDataTables::GetTableInfo method [.NET Framework metadata]
- GetTableInfo method [.NET Framework metadata]
ms.assetid: 50cbe557-2322-41aa-8e0d-f967602eaa0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82c88c75d5799134d8c683c91e28f956743b84ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992222"
---
# <a name="imetadatatablesgettableinfo-method"></a><span data-ttu-id="ff613-102">IMetaDataTables::GetTableInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="ff613-102">IMetaDataTables::GetTableInfo Method</span></span>
<span data-ttu-id="ff613-103">Získá název, velikost řádku, počet řádků, počet sloupců a index klíčový sloupec ze zadané tabulky.</span><span class="sxs-lookup"><span data-stu-id="ff613-103">Gets the name, row size, number of rows, number of columns, and key column index of the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff613-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff613-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ff613-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff613-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="ff613-106">[in] Identifikátor tabulky, jehož vlastnosti chcete vrátit.</span><span class="sxs-lookup"><span data-stu-id="ff613-106">[in] The identifier of the table whose properties to return.</span></span>  
  
 `pcbRow`  
 <span data-ttu-id="ff613-107">[out] Ukazatel na velikost v bajtech řádek tabulky.</span><span class="sxs-lookup"><span data-stu-id="ff613-107">[out] A pointer to the size, in bytes, of a table row.</span></span>  
  
 `pcRows`  
 <span data-ttu-id="ff613-108">[out] Ukazatel na počet řádků v tabulce.</span><span class="sxs-lookup"><span data-stu-id="ff613-108">[out] A pointer to the number of rows in the table.</span></span>  
  
 `pcCols`  
 <span data-ttu-id="ff613-109">[out] Ukazatel na počet sloupců v tabulce.</span><span class="sxs-lookup"><span data-stu-id="ff613-109">[out] A pointer to the number of columns in the table.</span></span>  
  
 `piKey`  
 <span data-ttu-id="ff613-110">[out] Ukazatel na index klíčový sloupec nebo -1, pokud tabulka nemá žádný klíčový sloupec.</span><span class="sxs-lookup"><span data-stu-id="ff613-110">[out] A pointer to the index of the key column, or -1 if the table has no key column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="ff613-111">[out] Ukazatel na ukazatel na název tabulky.</span><span class="sxs-lookup"><span data-stu-id="ff613-111">[out] A pointer to a pointer to the table name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff613-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff613-112">Requirements</span></span>  
 <span data-ttu-id="ff613-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff613-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff613-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ff613-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ff613-115">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ff613-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ff613-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff613-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff613-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff613-117">See also</span></span>

- [<span data-ttu-id="ff613-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff613-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="ff613-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff613-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
