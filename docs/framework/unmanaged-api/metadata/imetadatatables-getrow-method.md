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
ms.openlocfilehash: 13d514157382c75a2eb9799837f9355d0e469c99
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84489896"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="de996-102">IMetaDataTables::GetRow – metoda</span><span class="sxs-lookup"><span data-stu-id="de996-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="de996-103">Získá řádek v zadaném indexu řádku v tabulce se zadaným indexem tabulky.</span><span class="sxs-lookup"><span data-stu-id="de996-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de996-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de996-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de996-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="de996-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="de996-106">pro Index tabulky, ze které se má řádek načíst</span><span class="sxs-lookup"><span data-stu-id="de996-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="de996-107">pro Index řádku, který se má načíst</span><span class="sxs-lookup"><span data-stu-id="de996-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="de996-108">mimo Ukazatel na ukazatel na řádek.</span><span class="sxs-lookup"><span data-stu-id="de996-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de996-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="de996-109">Remarks</span></span>  

  <span data-ttu-id="de996-110">Nedoporučujeme používat tuto metodu, protože nevrací konzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="de996-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="de996-111">Informace o tabulce identifikátorů GUID najdete v dokumentaci k Common Language Infrastructure (CLI), zejména v oddílu oddíl II: definice metadat a sémantika.</span><span class="sxs-lookup"><span data-stu-id="de996-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="de996-112">Dokumentace je k dispozici online; viz [ECMA C# a Common Language Infrastructure standardy](../../../standard/components.md#applicable-standards) a [standardní ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="de996-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de996-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="de996-113">Requirements</span></span>  
 <span data-ttu-id="de996-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de996-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de996-115">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="de996-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="de996-116">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="de996-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="de996-117">**Verze .NET Framework**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de996-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de996-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de996-118">See also</span></span>

- [<span data-ttu-id="de996-119">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="de996-119">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="de996-120">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="de996-120">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
