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
ms.openlocfilehash: 954b4df6b341e18c5a995b57541a72e236278c45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449592"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="8c8ca-102">IMetaDataTables::GetRow – metoda</span><span class="sxs-lookup"><span data-stu-id="8c8ca-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="8c8ca-103">Získá řádek indexem zadaný řádek v tabulce u zadané tabulky indexu.</span><span class="sxs-lookup"><span data-stu-id="8c8ca-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c8ca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c8ca-104">Syntax</span></span>  
  
```  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c8ca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c8ca-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="8c8ca-106">[v] Index v tabulce, ze kterého se načíst řádek.</span><span class="sxs-lookup"><span data-stu-id="8c8ca-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="8c8ca-107">[v] Index řádku, který má získat.</span><span class="sxs-lookup"><span data-stu-id="8c8ca-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="8c8ca-108">[out] Ukazatel na ukazatel na řádek.</span><span class="sxs-lookup"><span data-stu-id="8c8ca-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c8ca-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c8ca-109">Remarks</span></span>  
 <span data-ttu-id="8c8ca-110">Nedoporučujeme použití této metody, protože nevrací konzistentních výsledků.</span><span class="sxs-lookup"><span data-stu-id="8c8ca-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="8c8ca-111">Informace o tabulce GUID najdete v dokumentaci společné jazykové infrastruktury (CLI), zejména "oddílu II: Metadata definice a sémantiku".</span><span class="sxs-lookup"><span data-stu-id="8c8ca-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="8c8ca-112">Dokumentace je k dispozici online; v tématu [ECMA C# a společné jazykové infrastruktury normy](http://go.microsoft.com/fwlink/?LinkID=99212) na webu MSDN a [standardní standardy ECMA-335 - společné jazykové infrastruktury (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) na webu Ecma mezinárodní.</span><span class="sxs-lookup"><span data-stu-id="8c8ca-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c8ca-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c8ca-113">Requirements</span></span>  
 <span data-ttu-id="8c8ca-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c8ca-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c8ca-115">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8c8ca-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8c8ca-116">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c8ca-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8c8ca-117">**Verze rozhraní .NET framework**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c8ca-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c8ca-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c8ca-118">See Also</span></span>  
 [<span data-ttu-id="8c8ca-119">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c8ca-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="8c8ca-120">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c8ca-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
