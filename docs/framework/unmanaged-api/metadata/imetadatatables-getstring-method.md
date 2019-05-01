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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8fed98521c0609ebd8b5f65885d69c77814e9e85
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042286"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="f38a2-102">IMetaDataTables::GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="f38a2-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="f38a2-103">Získá řetězec v zadaném indexu ze sloupce tabulky v aktuálním oboru odkaz.</span><span class="sxs-lookup"><span data-stu-id="f38a2-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f38a2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f38a2-104">Syntax</span></span>  
  
```  
HRESULT GetString (   
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f38a2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f38a2-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="f38a2-106">[in] Index, na kterém spustíte hledání další hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f38a2-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="f38a2-107">[out] Ukazatel na ukazatel na hodnotu vráceného řetězce.</span><span class="sxs-lookup"><span data-stu-id="f38a2-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f38a2-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f38a2-108">Requirements</span></span>  
 <span data-ttu-id="f38a2-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f38a2-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f38a2-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f38a2-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f38a2-111">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f38a2-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f38a2-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f38a2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f38a2-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f38a2-113">See also</span></span>

- [<span data-ttu-id="f38a2-114">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f38a2-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="f38a2-115">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f38a2-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
