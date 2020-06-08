---
title: IMetaDataTables::GetNextGuid – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextGuid
helpviewer_keywords:
- GetNextGuid method [.NET Framework metadata]
- IMetaDataTables::GetNextGuid method [.NET Framework metadata]
ms.assetid: 68f6ea4d-9112-4d6b-93d9-e34f1e2f2496
topic_type:
- apiref
ms.openlocfilehash: 645a9913d0de6f93e59df3dd8ba7267ddb13b41b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490234"
---
# <a name="imetadatatablesgetnextguid-method"></a><span data-ttu-id="f2373-102">IMetaDataTables::GetNextGuid – metoda</span><span class="sxs-lookup"><span data-stu-id="f2373-102">IMetaDataTables::GetNextGuid Method</span></span>
<span data-ttu-id="f2373-103">Získá index další hodnoty GUID ve sloupci aktuální tabulky.</span><span class="sxs-lookup"><span data-stu-id="f2373-103">Gets the index of the next GUID value in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2373-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2373-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2373-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2373-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="f2373-106">pro Hodnota indexu ze sloupce tabulky identifikátorů GUID</span><span class="sxs-lookup"><span data-stu-id="f2373-106">[in] The index value from a GUID table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="f2373-107">mimo Ukazatel na index další hodnoty GUID.</span><span class="sxs-lookup"><span data-stu-id="f2373-107">[out] A pointer to the index of the next GUID value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2373-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f2373-108">Remarks</span></span>  

  <span data-ttu-id="f2373-109">Nedoporučujeme používat tuto metodu, protože nevrací konzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="f2373-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="f2373-110">Informace o tabulce identifikátorů GUID najdete v dokumentaci k Common Language Infrastructure (CLI), zejména v oddílu oddíl II: definice metadat a sémantika.</span><span class="sxs-lookup"><span data-stu-id="f2373-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="f2373-111">Dokumentace je k dispozici online; viz [ECMA C# a Common Language Infrastructure standardy](../../../standard/components.md#applicable-standards) a [standardní ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="f2373-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2373-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f2373-112">Requirements</span></span>  
 <span data-ttu-id="f2373-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2373-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2373-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f2373-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f2373-115">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="f2373-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f2373-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2373-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2373-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2373-117">See also</span></span>

- [<span data-ttu-id="f2373-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f2373-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="f2373-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f2373-119">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
