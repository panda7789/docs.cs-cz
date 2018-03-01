---
title: "IMetaDataTables::GetNextGuid – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataTables.GetNextGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextGuid
helpviewer_keywords:
- GetNextGuid method [.NET Framework metadata]
- IMetaDataTables::GetNextGuid method [.NET Framework metadata]
ms.assetid: 68f6ea4d-9112-4d6b-93d9-e34f1e2f2496
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8d3585778d9076cb313ffed69a0e126891c4ce49
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetnextguid-method"></a><span data-ttu-id="3ff52-102">IMetaDataTables::GetNextGuid – metoda</span><span class="sxs-lookup"><span data-stu-id="3ff52-102">IMetaDataTables::GetNextGuid Method</span></span>
<span data-ttu-id="3ff52-103">Získá index další hodnota identifikátoru GUID v aktuální sloupec tabulky.</span><span class="sxs-lookup"><span data-stu-id="3ff52-103">Gets the index of the next GUID value in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ff52-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ff52-104">Syntax</span></span>  
  
```  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3ff52-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ff52-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="3ff52-106">[v] Hodnota indexu sloupcem tabulky identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="3ff52-106">[in] The index value from a GUID table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="3ff52-107">[out] Ukazatel na index další hodnota identifikátoru GUID.</span><span class="sxs-lookup"><span data-stu-id="3ff52-107">[out] A pointer to the index of the next GUID value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ff52-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ff52-108">Remarks</span></span>  
 <span data-ttu-id="3ff52-109">Nedoporučujeme použití této metody, protože nevrací konzistentních výsledků.</span><span class="sxs-lookup"><span data-stu-id="3ff52-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="3ff52-110">Informace o tabulce GUID najdete v dokumentaci společné jazykové infrastruktury (CLI), zejména "oddílu II: Metadata definice a sémantiku".</span><span class="sxs-lookup"><span data-stu-id="3ff52-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="3ff52-111">Dokumentace je k dispozici online; v tématu [ECMA C# a společné jazykové infrastruktury normy](http://go.microsoft.com/fwlink/?LinkID=99212) na webu MSDN a [standardní standardy ECMA-335 - společné jazykové infrastruktury (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) na webu Ecma mezinárodní.</span><span class="sxs-lookup"><span data-stu-id="3ff52-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ff52-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3ff52-112">Requirements</span></span>  
 <span data-ttu-id="3ff52-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ff52-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ff52-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3ff52-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3ff52-115">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3ff52-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3ff52-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ff52-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ff52-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ff52-117">See Also</span></span>  
 [<span data-ttu-id="3ff52-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3ff52-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="3ff52-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3ff52-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
