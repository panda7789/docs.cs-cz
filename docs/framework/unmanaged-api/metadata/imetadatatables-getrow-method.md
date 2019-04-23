---
title: IMetaDataTables::GetRow – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a02719651d8169c1122f5a46b1b8df39b28612ea
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197279"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="31c68-102">IMetaDataTables::GetRow – metoda</span><span class="sxs-lookup"><span data-stu-id="31c68-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="31c68-103">Získá řádek indexu zadaný řádek v tabulce indexu zadané tabulky.</span><span class="sxs-lookup"><span data-stu-id="31c68-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31c68-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31c68-104">Syntax</span></span>  
  
```  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31c68-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="31c68-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="31c68-106">[in] Index tabulky, ze kterého se budou načítat řádku.</span><span class="sxs-lookup"><span data-stu-id="31c68-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="31c68-107">[in] Index řádku, který má získat.</span><span class="sxs-lookup"><span data-stu-id="31c68-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="31c68-108">[out] Ukazatel na ukazatel na řádku.</span><span class="sxs-lookup"><span data-stu-id="31c68-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31c68-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="31c68-109">Remarks</span></span>  
 <span data-ttu-id="31c68-110">Nedoporučujeme použití této metody, protože nevrací konzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="31c68-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="31c68-111">Informace o tabulce GUID najdete v dokumentaci společné jazykové infrastruktury (CLI), zejména "oddíl II: Definice metadat a sémantika".</span><span class="sxs-lookup"><span data-stu-id="31c68-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="31c68-112">Dokumentace je k dispozici online; Zobrazit [ECMA C# a společné normy jazykové infrastruktury](https://go.microsoft.com/fwlink/?LinkID=99212) na webu MSDN a [Standard ECMA-335 – společné jazykové infrastruktury (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) na webu Ecma International.</span><span class="sxs-lookup"><span data-stu-id="31c68-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31c68-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="31c68-113">Requirements</span></span>  
 <span data-ttu-id="31c68-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31c68-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31c68-115">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="31c68-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31c68-116">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="31c68-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="31c68-117">**Verze rozhraní .NET framework**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31c68-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31c68-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31c68-118">See also</span></span>

- [<span data-ttu-id="31c68-119">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="31c68-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="31c68-120">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="31c68-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
