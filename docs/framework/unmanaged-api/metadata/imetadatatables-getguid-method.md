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
ms.openlocfilehash: 94df2192b0b02f6cf0e068cb554afc6e7f9ec74d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486937"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="49192-102">IMetaDataTables::GetGuid – metoda</span><span class="sxs-lookup"><span data-stu-id="49192-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="49192-103">Získá identifikátor GUID z řádku v zadaném indexu.</span><span class="sxs-lookup"><span data-stu-id="49192-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49192-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49192-104">Syntax</span></span>  
  
```  
HRESULT GetGuid (   
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49192-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="49192-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="49192-106">[in] Index řádku, od kterého se má získat identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="49192-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="49192-107">[out] Ukazatel na ukazatel na identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="49192-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49192-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="49192-108">Remarks</span></span>  
 <span data-ttu-id="49192-109">Nedoporučujeme použití této metody, protože nevrací konzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="49192-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="49192-110">Informace o tabulce GUID najdete v dokumentaci společné jazykové infrastruktury (CLI), zejména "oddíl II: Definice metadat a sémantika".</span><span class="sxs-lookup"><span data-stu-id="49192-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="49192-111">Dokumentace je k dispozici online; Zobrazit [ECMA C# a společné normy jazykové infrastruktury](https://go.microsoft.com/fwlink/?LinkID=99212) na webu MSDN a [Standard ECMA-335 – společné jazykové infrastruktury (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) na webu Ecma International.</span><span class="sxs-lookup"><span data-stu-id="49192-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49192-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="49192-112">Requirements</span></span>  
 <span data-ttu-id="49192-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49192-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49192-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="49192-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="49192-115">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="49192-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="49192-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49192-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49192-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49192-117">See also</span></span>
- [<span data-ttu-id="49192-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="49192-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="49192-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="49192-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
