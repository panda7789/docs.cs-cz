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
ms.openlocfilehash: a1cd932051a9ed90a29ff5eeaa818a67104192bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175249"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="92e09-102">IMetaDataTables::GetNextString – metoda</span><span class="sxs-lookup"><span data-stu-id="92e09-102">IMetaDataTables::GetNextString Method</span></span>
<span data-ttu-id="92e09-103">Získá index dalšího řetězce v aktuálním sloupci tabulky.</span><span class="sxs-lookup"><span data-stu-id="92e09-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92e09-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92e09-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextString (
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92e09-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92e09-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="92e09-106">[v] Hodnota indexu ze sloupce tabulky řetězců.</span><span class="sxs-lookup"><span data-stu-id="92e09-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="92e09-107">[out] Ukazatel na index dalšího řetězce ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="92e09-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92e09-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="92e09-108">Requirements</span></span>  
 <span data-ttu-id="92e09-109">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92e09-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92e09-110">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="92e09-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="92e09-111">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="92e09-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="92e09-112">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92e09-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92e09-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="92e09-113">See also</span></span>

- [<span data-ttu-id="92e09-114">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92e09-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="92e09-115">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92e09-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
