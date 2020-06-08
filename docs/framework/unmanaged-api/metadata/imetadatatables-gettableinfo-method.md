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
ms.openlocfilehash: 7e60dd9535809ca13f3bbe6ac76f5ea1209df734
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501163"
---
# <a name="imetadatatablesgettableinfo-method"></a><span data-ttu-id="7f029-102">IMetaDataTables::GetTableInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="7f029-102">IMetaDataTables::GetTableInfo Method</span></span>
<span data-ttu-id="7f029-103">Získá název, velikost řádku, počet řádků, počet sloupců a klíčový index sloupce zadané tabulky.</span><span class="sxs-lookup"><span data-stu-id="7f029-103">Gets the name, row size, number of rows, number of columns, and key column index of the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f029-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f029-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="7f029-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f029-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="7f029-106">pro Identifikátor tabulky, jejíž vlastnosti se mají vrátit</span><span class="sxs-lookup"><span data-stu-id="7f029-106">[in] The identifier of the table whose properties to return.</span></span>  
  
 `pcbRow`  
 <span data-ttu-id="7f029-107">mimo Ukazatel na velikost řádku tabulky v bajtech.</span><span class="sxs-lookup"><span data-stu-id="7f029-107">[out] A pointer to the size, in bytes, of a table row.</span></span>  
  
 `pcRows`  
 <span data-ttu-id="7f029-108">mimo Ukazatel na počet řádků v tabulce.</span><span class="sxs-lookup"><span data-stu-id="7f029-108">[out] A pointer to the number of rows in the table.</span></span>  
  
 `pcCols`  
 <span data-ttu-id="7f029-109">mimo Ukazatel na počet sloupců v tabulce.</span><span class="sxs-lookup"><span data-stu-id="7f029-109">[out] A pointer to the number of columns in the table.</span></span>  
  
 `piKey`  
 <span data-ttu-id="7f029-110">mimo Ukazatel na index sloupce klíče nebo hodnotu-1, pokud tabulka neobsahuje žádný klíčový sloupec.</span><span class="sxs-lookup"><span data-stu-id="7f029-110">[out] A pointer to the index of the key column, or -1 if the table has no key column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="7f029-111">mimo Ukazatel na ukazatel na název tabulky.</span><span class="sxs-lookup"><span data-stu-id="7f029-111">[out] A pointer to a pointer to the table name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f029-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f029-112">Requirements</span></span>  
 <span data-ttu-id="7f029-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f029-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f029-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7f029-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f029-115">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="7f029-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7f029-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f029-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f029-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f029-117">See also</span></span>

- [<span data-ttu-id="7f029-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f029-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="7f029-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f029-119">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
