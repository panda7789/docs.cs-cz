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
ms.openlocfilehash: 41e7b8193ce3288d526db8d7d8c289b0a053ee4e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84489753"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="ebbfb-102">IMetaDataTables::GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="ebbfb-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="ebbfb-103">Získá řetězec na zadaném indexu ze sloupce tabulky v aktuálním oboru odkazů.</span><span class="sxs-lookup"><span data-stu-id="ebbfb-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebbfb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebbfb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebbfb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ebbfb-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="ebbfb-106">pro Index, ve kterém se má spustit hledání další hodnoty</span><span class="sxs-lookup"><span data-stu-id="ebbfb-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="ebbfb-107">mimo Ukazatel na ukazatel na vrácenou hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="ebbfb-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebbfb-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ebbfb-108">Requirements</span></span>  
 <span data-ttu-id="ebbfb-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebbfb-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebbfb-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ebbfb-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ebbfb-111">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="ebbfb-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ebbfb-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebbfb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebbfb-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ebbfb-113">See also</span></span>

- [<span data-ttu-id="ebbfb-114">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ebbfb-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="ebbfb-115">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ebbfb-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
