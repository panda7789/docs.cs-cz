---
title: IMetaDataTables::GetNextBlob – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextBlob
helpviewer_keywords:
- IMetaDataTables::GetNextBlob method [.NET Framework metadata]
- GetNextBlob method [.NET Framework metadata]
ms.assetid: 017c8ab4-4c09-4754-9935-5b0b49cabecb
topic_type:
- apiref
ms.openlocfilehash: 086448248364403b718408ad8bd32e48447742d0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490378"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="d3a79-102">IMetaDataTables::GetNextBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="d3a79-102">IMetaDataTables::GetNextBlob Method</span></span>
<span data-ttu-id="d3a79-103">Získá index dalšího binárního rozsáhlého objektu (BLOB) v tabulce.</span><span class="sxs-lookup"><span data-stu-id="d3a79-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3a79-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3a79-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3a79-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3a79-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="d3a79-106">pro Index vrácený ze sloupce objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="d3a79-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="d3a79-107">mimo Ukazatel na index dalšího objektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="d3a79-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3a79-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d3a79-108">Requirements</span></span>  
 <span data-ttu-id="d3a79-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3a79-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3a79-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d3a79-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d3a79-111">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="d3a79-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d3a79-112">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3a79-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3a79-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3a79-113">See also</span></span>

- [<span data-ttu-id="d3a79-114">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3a79-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="d3a79-115">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3a79-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
