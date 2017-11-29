---
title: "IMetaDataTables::GetRow – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetRow
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 281824ace7696ab0fc6b3a96e0cdf307a9419313
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="d286a-102">IMetaDataTables::GetRow – metoda</span><span class="sxs-lookup"><span data-stu-id="d286a-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="d286a-103">Získá řádek indexem zadaný řádek v tabulce u zadané tabulky indexu.</span><span class="sxs-lookup"><span data-stu-id="d286a-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d286a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d286a-104">Syntax</span></span>  
  
```  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d286a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d286a-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="d286a-106">[v] Index v tabulce, ze kterého se načíst řádek.</span><span class="sxs-lookup"><span data-stu-id="d286a-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="d286a-107">[v] Index řádku, který má získat.</span><span class="sxs-lookup"><span data-stu-id="d286a-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="d286a-108">[out] Ukazatel na ukazatel na řádek.</span><span class="sxs-lookup"><span data-stu-id="d286a-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d286a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d286a-109">Remarks</span></span>  
 <span data-ttu-id="d286a-110">Nedoporučujeme použití této metody, protože nevrací konzistentních výsledků.</span><span class="sxs-lookup"><span data-stu-id="d286a-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="d286a-111">Informace o tabulce GUID najdete v dokumentaci společné jazykové infrastruktury (CLI), zejména "oddílu II: Metadata definice a sémantiku".</span><span class="sxs-lookup"><span data-stu-id="d286a-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="d286a-112">Dokumentace je k dispozici online; v tématu [ECMA C# a společné jazykové infrastruktury normy](http://go.microsoft.com/fwlink/?LinkID=99212) na webu MSDN a [standardní standardy ECMA-335 - společné jazykové infrastruktury (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) na webu Ecma mezinárodní.</span><span class="sxs-lookup"><span data-stu-id="d286a-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d286a-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d286a-113">Requirements</span></span>  
 <span data-ttu-id="d286a-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d286a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d286a-115">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d286a-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d286a-116">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d286a-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d286a-117">**Verze rozhraní .NET framework**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d286a-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d286a-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="d286a-118">See Also</span></span>  
 [<span data-ttu-id="d286a-119">Imetadatatables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d286a-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="d286a-120">Imetadatatables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d286a-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
