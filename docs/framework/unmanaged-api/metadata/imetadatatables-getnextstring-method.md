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
ms.openlocfilehash: 6f4764f016360a2ec0ab054b7a89ccb3f86aeb43
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490221"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="25130-102">IMetaDataTables::GetNextString – metoda</span><span class="sxs-lookup"><span data-stu-id="25130-102">IMetaDataTables::GetNextString Method</span></span>
<span data-ttu-id="25130-103">Získá index dalšího řetězce ve sloupci aktuální tabulky.</span><span class="sxs-lookup"><span data-stu-id="25130-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25130-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25130-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextString (
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25130-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25130-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="25130-106">pro Hodnota indexu ze sloupce tabulky řetězců.</span><span class="sxs-lookup"><span data-stu-id="25130-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="25130-107">mimo Ukazatel na index dalšího řetězce ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="25130-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25130-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25130-108">Requirements</span></span>  
 <span data-ttu-id="25130-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25130-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25130-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="25130-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="25130-111">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="25130-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="25130-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25130-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25130-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25130-113">See also</span></span>

- [<span data-ttu-id="25130-114">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25130-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="25130-115">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25130-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
