---
title: "IMetaDataTables::GetString – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetString
helpviewer_keywords:
- IMetaDataTables::GetString method [.NET Framework metadata]
- GetString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 895c35cf-b95d-4e3b-93b5-cfc1cf9044fc
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 687380d3a09a80db216aafbf1ee84c76e31bbf36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="1090b-102">IMetaDataTables::GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="1090b-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="1090b-103">Získá řetězec v zadaném indexu ze sloupce tabulky v aktuálním oboru odkaz.</span><span class="sxs-lookup"><span data-stu-id="1090b-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1090b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1090b-104">Syntax</span></span>  
  
```  
HRESULT GetString (   
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1090b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1090b-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="1090b-106">[v] Index, od kterého má začít k vyhledání další hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1090b-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="1090b-107">[out] Ukazatel na ukazatel na hodnotu vrácený řetězec.</span><span class="sxs-lookup"><span data-stu-id="1090b-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1090b-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1090b-108">Requirements</span></span>  
 <span data-ttu-id="1090b-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1090b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1090b-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1090b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1090b-111">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1090b-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1090b-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1090b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1090b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="1090b-113">See Also</span></span>  
 [<span data-ttu-id="1090b-114">Imetadatatables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1090b-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="1090b-115">Imetadatatables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1090b-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
