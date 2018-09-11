---
title: IMetaDataTables::GetGuid – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f589225dde1ba2aabc4ca32542339a771c3287d4
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44368572"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="d5ff2-102">IMetaDataTables::GetGuid – metoda</span><span class="sxs-lookup"><span data-stu-id="d5ff2-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="d5ff2-103">Získá identifikátor GUID z řádku v zadaném indexu.</span><span class="sxs-lookup"><span data-stu-id="d5ff2-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5ff2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5ff2-104">Syntax</span></span>  
  
```  
HRESULT GetGuid (   
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5ff2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5ff2-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="d5ff2-106">[in] Index řádku, od kterého se má získat identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="d5ff2-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="d5ff2-107">[out] Ukazatel na ukazatel na identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="d5ff2-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5ff2-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d5ff2-108">Remarks</span></span>  
 <span data-ttu-id="d5ff2-109">Nedoporučujeme použití této metody, protože nevrací konzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="d5ff2-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="d5ff2-110">Informace o tabulce GUID najdete v dokumentaci společné jazykové infrastruktury (CLI), zejména "oddíl II: Metadata definice a sémantika".</span><span class="sxs-lookup"><span data-stu-id="d5ff2-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="d5ff2-111">Dokumentace je k dispozici online; Zobrazit [ECMA C# a společné normy jazykové infrastruktury](https://go.microsoft.com/fwlink/?LinkID=99212) na webu MSDN a [Standard ECMA-335 – společné jazykové infrastruktury (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) na webu Ecma International.</span><span class="sxs-lookup"><span data-stu-id="d5ff2-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5ff2-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5ff2-112">Requirements</span></span>  
 <span data-ttu-id="d5ff2-113">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5ff2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5ff2-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d5ff2-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d5ff2-115">**Knihovna:** použit jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d5ff2-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d5ff2-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5ff2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5ff2-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5ff2-117">See Also</span></span>  
 [<span data-ttu-id="d5ff2-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5ff2-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="d5ff2-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5ff2-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
