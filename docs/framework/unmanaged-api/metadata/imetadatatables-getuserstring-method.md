---
title: "IMetaDataTables::GetUserString – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetUserString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetUserString
helpviewer_keywords:
- IMetaDataTables::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 35b8f0d6-9aba-4714-adb2-62020a38fb7e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 648cc9e6f947f5eaf5dd6c9354ba305f7ca0d530
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetuserstring-method"></a><span data-ttu-id="397dd-102">IMetaDataTables::GetUserString – metoda</span><span class="sxs-lookup"><span data-stu-id="397dd-102">IMetaDataTables::GetUserString Method</span></span>
<span data-ttu-id="397dd-103">Získá řetězec pevně v zadaném indexu ve sloupci řetězce v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="397dd-103">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="397dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="397dd-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
    [in]  ULONG       ixUserString,  
    [out] ULONG       *pcbData,  
    [out] const void  **ppData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="397dd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="397dd-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="397dd-106">[v] Hodnotu indexu, ve kterém budou načteny pevně řetězce.</span><span class="sxs-lookup"><span data-stu-id="397dd-106">[in] The index value from which the hard-coded string will be retrieved.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="397dd-107">[out] P; ukazatele na velikost `ppData`.</span><span class="sxs-lookup"><span data-stu-id="397dd-107">[out] A p;ointer to the size of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="397dd-108">[out] Ukazatel na ukazatel na vrácený řetězec.</span><span class="sxs-lookup"><span data-stu-id="397dd-108">[out] A pointer to a pointer to the returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="397dd-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="397dd-109">Requirements</span></span>  
 <span data-ttu-id="397dd-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="397dd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="397dd-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="397dd-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="397dd-112">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="397dd-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="397dd-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="397dd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="397dd-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="397dd-114">See Also</span></span>  
 [<span data-ttu-id="397dd-115">Imetadatatables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="397dd-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="397dd-116">Imetadatatables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="397dd-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
