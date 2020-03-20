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
ms.openlocfilehash: 57df124f15f78daad053d9634e1baa969a65cc35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175275"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="671e7-102">IMetaDataTables::GetGuid – metoda</span><span class="sxs-lookup"><span data-stu-id="671e7-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="671e7-103">Získá identifikátor GUID z řádku na zadaný index.</span><span class="sxs-lookup"><span data-stu-id="671e7-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="671e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="671e7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="671e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="671e7-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="671e7-106">[v] Index řádku, ze kterého chcete získat identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="671e7-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="671e7-107">[out] Ukazatel na ukazatel na identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="671e7-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="671e7-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="671e7-108">Remarks</span></span>  

  <span data-ttu-id="671e7-109">Nedoporučujeme použití této metody, protože nevrací konzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="671e7-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="671e7-110">Informace o tabulce GUID naleznete v dokumentaci cli (Common Language Infrastructure), zejména "Oddíl II: Definice metadat a sémantika".</span><span class="sxs-lookup"><span data-stu-id="671e7-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="671e7-111">Dokumentace je k dispozici online; viz [ecma c# a obecné standardy jazykové infrastruktury](../../../standard/components.md#applicable-standards) a [standardní ECMA-335 – common language infrastructure (CLI).](http://www.ecma-international.org/publications/standards/Ecma-335.htm)</span><span class="sxs-lookup"><span data-stu-id="671e7-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="671e7-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="671e7-112">Requirements</span></span>  
 <span data-ttu-id="671e7-113">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="671e7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="671e7-114">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="671e7-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="671e7-115">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="671e7-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="671e7-116">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="671e7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="671e7-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="671e7-117">See also</span></span>

- [<span data-ttu-id="671e7-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="671e7-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="671e7-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="671e7-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
