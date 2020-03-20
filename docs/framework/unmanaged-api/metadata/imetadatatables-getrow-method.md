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
ms.openlocfilehash: 71f6c496816fec1a7537f5ccdfdc1b47d17da871
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177108"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="1589f-102">IMetaDataTables::GetRow – metoda</span><span class="sxs-lookup"><span data-stu-id="1589f-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="1589f-103">Získá řádek na zadaný řádek indexu, v tabulce v zadaném indexu tabulky.</span><span class="sxs-lookup"><span data-stu-id="1589f-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1589f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1589f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1589f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1589f-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="1589f-106">[v] Index tabulky, ze kterého bude řádek načten.</span><span class="sxs-lookup"><span data-stu-id="1589f-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="1589f-107">[v] Index řádku získat.</span><span class="sxs-lookup"><span data-stu-id="1589f-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="1589f-108">[out] Ukazatel na ukazatel na řádek.</span><span class="sxs-lookup"><span data-stu-id="1589f-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1589f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1589f-109">Remarks</span></span>  

  <span data-ttu-id="1589f-110">Nedoporučujeme použití této metody, protože nevrací konzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="1589f-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="1589f-111">Informace o tabulce GUID naleznete v dokumentaci cli (Common Language Infrastructure), zejména "Oddíl II: Definice metadat a sémantika".</span><span class="sxs-lookup"><span data-stu-id="1589f-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="1589f-112">Dokumentace je k dispozici online; viz [ecma c# a obecné standardy jazykové infrastruktury](../../../standard/components.md#applicable-standards) a [standardní ECMA-335 – common language infrastructure (CLI).](http://www.ecma-international.org/publications/standards/Ecma-335.htm)</span><span class="sxs-lookup"><span data-stu-id="1589f-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1589f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1589f-113">Requirements</span></span>  
 <span data-ttu-id="1589f-114">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1589f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1589f-115">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="1589f-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1589f-116">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1589f-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1589f-117">**Verze rozhraní .NET Framework**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1589f-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1589f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="1589f-118">See also</span></span>

- [<span data-ttu-id="1589f-119">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1589f-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="1589f-120">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1589f-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
