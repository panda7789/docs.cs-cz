---
title: IMetaDataTables::GetNextString – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextString
helpviewer_keywords:
- IMetaDataTables::GetNextString method [.NET Framework metadata]
- GetNextString method [.NET Framework metadata]
ms.assetid: d9720428-c353-4f07-a7e8-899e106a1b37
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3c2008556ebf1b1961aef7dc0f24fd0a3161d06e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781451"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="b4be3-102">IMetaDataTables::GetNextString – metoda</span><span class="sxs-lookup"><span data-stu-id="b4be3-102">IMetaDataTables::GetNextString Method</span></span>
<span data-ttu-id="b4be3-103">Získá index další řetězce v aktuálním sloupci tabulky.</span><span class="sxs-lookup"><span data-stu-id="b4be3-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4be3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4be3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextString (   
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4be3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4be3-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="b4be3-106">[in] Hodnota indexu v tabulce sloupec řetězcového typu.</span><span class="sxs-lookup"><span data-stu-id="b4be3-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="b4be3-107">[out] Ukazatel na index další řetězec ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="b4be3-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4be3-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b4be3-108">Requirements</span></span>  
 <span data-ttu-id="b4be3-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4be3-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4be3-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b4be3-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b4be3-111">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b4be3-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b4be3-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4be3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4be3-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4be3-113">See also</span></span>

- [<span data-ttu-id="b4be3-114">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4be3-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="b4be3-115">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4be3-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
