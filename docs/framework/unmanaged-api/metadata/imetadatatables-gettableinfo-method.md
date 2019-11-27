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
ms.openlocfilehash: 662b628f3cc6d2d7138f56820beaccee9c5d9e81
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426656"
---
# <a name="imetadatatablesgettableinfo-method"></a><span data-ttu-id="c76de-102">IMetaDataTables::GetTableInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="c76de-102">IMetaDataTables::GetTableInfo Method</span></span>
<span data-ttu-id="c76de-103">Získá název, velikost řádku, počet řádků, počet sloupců a klíčový index sloupce zadané tabulky.</span><span class="sxs-lookup"><span data-stu-id="c76de-103">Gets the name, row size, number of rows, number of columns, and key column index of the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c76de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c76de-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c76de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c76de-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="c76de-106">pro Identifikátor tabulky, jejíž vlastnosti se mají vrátit</span><span class="sxs-lookup"><span data-stu-id="c76de-106">[in] The identifier of the table whose properties to return.</span></span>  
  
 `pcbRow`  
 <span data-ttu-id="c76de-107">mimo Ukazatel na velikost řádku tabulky v bajtech.</span><span class="sxs-lookup"><span data-stu-id="c76de-107">[out] A pointer to the size, in bytes, of a table row.</span></span>  
  
 `pcRows`  
 <span data-ttu-id="c76de-108">mimo Ukazatel na počet řádků v tabulce.</span><span class="sxs-lookup"><span data-stu-id="c76de-108">[out] A pointer to the number of rows in the table.</span></span>  
  
 `pcCols`  
 <span data-ttu-id="c76de-109">mimo Ukazatel na počet sloupců v tabulce.</span><span class="sxs-lookup"><span data-stu-id="c76de-109">[out] A pointer to the number of columns in the table.</span></span>  
  
 `piKey`  
 <span data-ttu-id="c76de-110">mimo Ukazatel na index sloupce klíče nebo hodnotu-1, pokud tabulka neobsahuje žádný klíčový sloupec.</span><span class="sxs-lookup"><span data-stu-id="c76de-110">[out] A pointer to the index of the key column, or -1 if the table has no key column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="c76de-111">mimo Ukazatel na ukazatel na název tabulky.</span><span class="sxs-lookup"><span data-stu-id="c76de-111">[out] A pointer to a pointer to the table name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c76de-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c76de-112">Requirements</span></span>  
 <span data-ttu-id="c76de-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c76de-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c76de-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c76de-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c76de-115">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="c76de-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c76de-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c76de-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c76de-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c76de-117">See also</span></span>

- [<span data-ttu-id="c76de-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c76de-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="c76de-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c76de-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
