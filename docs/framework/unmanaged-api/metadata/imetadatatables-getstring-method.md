---
title: IMetaDataTables::GetString – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetString
helpviewer_keywords:
- IMetaDataTables::GetString method [.NET Framework metadata]
- GetString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 895c35cf-b95d-4e3b-93b5-cfc1cf9044fc
topic_type:
- apiref
ms.openlocfilehash: 216a1f7bd2ff5a596fa7abf7874b5e603d5a9f7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175236"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="ffd9b-102">IMetaDataTables::GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="ffd9b-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="ffd9b-103">Získá řetězec na zadaný index ze sloupce tabulky v aktuálním referenčním oboru.</span><span class="sxs-lookup"><span data-stu-id="ffd9b-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffd9b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ffd9b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffd9b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ffd9b-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="ffd9b-106">[v] Index, ve kterém chcete začít hledat další hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ffd9b-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="ffd9b-107">[out] Ukazatel na ukazatel na vrácenou hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="ffd9b-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffd9b-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ffd9b-108">Requirements</span></span>  
 <span data-ttu-id="ffd9b-109">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffd9b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffd9b-110">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="ffd9b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ffd9b-111">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ffd9b-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ffd9b-112">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffd9b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffd9b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ffd9b-113">See also</span></span>

- [<span data-ttu-id="ffd9b-114">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ffd9b-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="ffd9b-115">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ffd9b-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
