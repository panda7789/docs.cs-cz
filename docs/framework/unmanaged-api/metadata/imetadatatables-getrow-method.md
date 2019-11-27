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
ms.openlocfilehash: 9973ef77a064dfe144d742d8cf12d8ae8dd2565f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447410"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="ada5c-102">IMetaDataTables::GetRow – metoda</span><span class="sxs-lookup"><span data-stu-id="ada5c-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="ada5c-103">Získá řádek v zadaném indexu řádku v tabulce se zadaným indexem tabulky.</span><span class="sxs-lookup"><span data-stu-id="ada5c-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ada5c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ada5c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ada5c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ada5c-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="ada5c-106">pro Index tabulky, ze které se má řádek načíst</span><span class="sxs-lookup"><span data-stu-id="ada5c-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="ada5c-107">pro Index řádku, který se má načíst</span><span class="sxs-lookup"><span data-stu-id="ada5c-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="ada5c-108">mimo Ukazatel na ukazatel na řádek.</span><span class="sxs-lookup"><span data-stu-id="ada5c-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ada5c-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ada5c-109">Remarks</span></span>  
 <span data-ttu-id="ada5c-110">Nedoporučujeme používat tuto metodu, protože nevrací konzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="ada5c-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="ada5c-111">Informace o tabulce identifikátorů GUID najdete v dokumentaci k Common Language Infrastructure (CLI), zejména v oddílu oddíl II: definice metadat a sémantika.</span><span class="sxs-lookup"><span data-stu-id="ada5c-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="ada5c-112">Dokumentace je k dispozici online; v [tématu C# ECMA a Common Language Infrastructure](https://go.microsoft.com/fwlink/?LinkID=99212) Standards na webu MSDN a na [Standard ECMA-335-Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) se na webu ECMA International.</span><span class="sxs-lookup"><span data-stu-id="ada5c-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ada5c-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ada5c-113">Requirements</span></span>  
 <span data-ttu-id="ada5c-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ada5c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ada5c-115">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ada5c-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ada5c-116">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="ada5c-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ada5c-117">**Verze .NET Framework**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ada5c-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ada5c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ada5c-118">See also</span></span>

- [<span data-ttu-id="ada5c-119">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ada5c-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="ada5c-120">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ada5c-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
