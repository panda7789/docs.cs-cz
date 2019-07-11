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
ms.openlocfilehash: 98fc95c618a7a06f5e6c219d7707af291770c06a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781416"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="fde51-102">IMetaDataTables::GetRow – metoda</span><span class="sxs-lookup"><span data-stu-id="fde51-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="fde51-103">Získá řádek indexu zadaný řádek v tabulce indexu zadané tabulky.</span><span class="sxs-lookup"><span data-stu-id="fde51-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fde51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fde51-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fde51-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fde51-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="fde51-106">[in] Index tabulky, ze kterého se budou načítat řádku.</span><span class="sxs-lookup"><span data-stu-id="fde51-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="fde51-107">[in] Index řádku, který má získat.</span><span class="sxs-lookup"><span data-stu-id="fde51-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="fde51-108">[out] Ukazatel na ukazatel na řádku.</span><span class="sxs-lookup"><span data-stu-id="fde51-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fde51-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fde51-109">Remarks</span></span>  
 <span data-ttu-id="fde51-110">Nedoporučujeme použití této metody, protože nevrací konzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="fde51-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="fde51-111">Informace o tabulce GUID najdete v dokumentaci společné jazykové infrastruktury (CLI), zejména "oddíl II: Definice metadat a sémantika".</span><span class="sxs-lookup"><span data-stu-id="fde51-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="fde51-112">Dokumentace je k dispozici online; Zobrazit [ECMA C# a společné normy jazykové infrastruktury](https://go.microsoft.com/fwlink/?LinkID=99212) na webu MSDN a [Standard ECMA-335 – společné jazykové infrastruktury (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) na webu Ecma International.</span><span class="sxs-lookup"><span data-stu-id="fde51-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fde51-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fde51-113">Requirements</span></span>  
 <span data-ttu-id="fde51-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fde51-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fde51-115">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fde51-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fde51-116">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fde51-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fde51-117">**Verze rozhraní .NET framework**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fde51-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fde51-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fde51-118">See also</span></span>

- [<span data-ttu-id="fde51-119">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fde51-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="fde51-120">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fde51-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
