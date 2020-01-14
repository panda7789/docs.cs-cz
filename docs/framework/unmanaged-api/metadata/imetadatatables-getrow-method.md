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
ms.openlocfilehash: 9ac6eba18ae23dc80a8dc90383aa67cfe41b39ff
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937409"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="2f585-102">IMetaDataTables::GetRow – metoda</span><span class="sxs-lookup"><span data-stu-id="2f585-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="2f585-103">Získá řádek v zadaném indexu řádku v tabulce se zadaným indexem tabulky.</span><span class="sxs-lookup"><span data-stu-id="2f585-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f585-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f585-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f585-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f585-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="2f585-106">pro Index tabulky, ze které se má řádek načíst</span><span class="sxs-lookup"><span data-stu-id="2f585-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="2f585-107">pro Index řádku, který se má načíst</span><span class="sxs-lookup"><span data-stu-id="2f585-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="2f585-108">mimo Ukazatel na ukazatel na řádek.</span><span class="sxs-lookup"><span data-stu-id="2f585-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f585-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f585-109">Remarks</span></span>  

  <span data-ttu-id="2f585-110">Nedoporučujeme používat tuto metodu, protože nevrací konzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="2f585-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="2f585-111">Informace o tabulce identifikátorů GUID najdete v dokumentaci k Common Language Infrastructure (CLI), zejména v oddílu oddíl II: definice metadat a sémantika.</span><span class="sxs-lookup"><span data-stu-id="2f585-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="2f585-112">Dokumentace je k dispozici online; viz [ECMA C# a Common Language Infrastructure standardy](../../../standard/components.md#applicable-standards) a [standardní ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="2f585-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f585-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f585-113">Requirements</span></span>  
 <span data-ttu-id="2f585-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f585-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f585-115">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2f585-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2f585-116">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="2f585-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2f585-117">**Verze .NET Framework**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f585-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f585-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f585-118">See also</span></span>

- [<span data-ttu-id="2f585-119">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f585-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="2f585-120">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f585-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
