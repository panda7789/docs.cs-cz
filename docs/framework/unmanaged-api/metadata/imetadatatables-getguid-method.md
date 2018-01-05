---
title: "IMetaDataTables::GetGuid – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetGuid
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58dbcb7ebf56f126d89a42a1f5df6247266cb38c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="8fc53-102">IMetaDataTables::GetGuid – metoda</span><span class="sxs-lookup"><span data-stu-id="8fc53-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="8fc53-103">Získá identifikátor GUID z řádek na pozici se zadaným indexem.</span><span class="sxs-lookup"><span data-stu-id="8fc53-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fc53-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fc53-104">Syntax</span></span>  
  
```  
HRESULT GetGuid (   
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8fc53-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8fc53-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="8fc53-106">[v] Index řádku, od kterého chcete získat identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="8fc53-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="8fc53-107">[out] Ukazatel na ukazatel na identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="8fc53-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fc53-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8fc53-108">Remarks</span></span>  
 <span data-ttu-id="8fc53-109">Nedoporučujeme použití této metody, protože nevrací konzistentních výsledků.</span><span class="sxs-lookup"><span data-stu-id="8fc53-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="8fc53-110">Informace o tabulce GUID najdete v dokumentaci společné jazykové infrastruktury (CLI), zejména "oddílu II: Metadata definice a sémantiku".</span><span class="sxs-lookup"><span data-stu-id="8fc53-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="8fc53-111">Dokumentace je k dispozici online; v tématu [ECMA C# a společné jazykové infrastruktury normy](http://go.microsoft.com/fwlink/?LinkID=99212) na webu MSDN a [standardní standardy ECMA-335 - společné jazykové infrastruktury (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) na webu Ecma mezinárodní.</span><span class="sxs-lookup"><span data-stu-id="8fc53-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fc53-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8fc53-112">Requirements</span></span>  
 <span data-ttu-id="8fc53-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fc53-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fc53-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8fc53-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8fc53-115">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8fc53-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8fc53-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fc53-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc53-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="8fc53-117">See Also</span></span>  
 [<span data-ttu-id="8fc53-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8fc53-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="8fc53-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8fc53-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
