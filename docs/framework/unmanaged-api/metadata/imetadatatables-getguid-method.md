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
ms.openlocfilehash: 6f273cb03ad00957afb2bd78fe538a940fae236a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501232"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="d2949-102">IMetaDataTables::GetGuid – metoda</span><span class="sxs-lookup"><span data-stu-id="d2949-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="d2949-103">Získá identifikátor GUID z řádku na zadaném indexu.</span><span class="sxs-lookup"><span data-stu-id="d2949-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2949-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2949-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2949-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2949-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="d2949-106">pro Index řádku, ze kterého se má získat identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="d2949-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="d2949-107">mimo Ukazatel na ukazatel na identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="d2949-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2949-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d2949-108">Remarks</span></span>  

  <span data-ttu-id="d2949-109">Nedoporučujeme používat tuto metodu, protože nevrací konzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="d2949-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="d2949-110">Informace o tabulce identifikátorů GUID najdete v dokumentaci k Common Language Infrastructure (CLI), zejména v oddílu oddíl II: definice metadat a sémantika.</span><span class="sxs-lookup"><span data-stu-id="d2949-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="d2949-111">Dokumentace je k dispozici online; viz [ECMA C# a Common Language Infrastructure standardy](../../../standard/components.md#applicable-standards) a [standardní ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="d2949-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2949-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2949-112">Requirements</span></span>  
 <span data-ttu-id="d2949-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2949-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2949-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d2949-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d2949-115">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="d2949-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d2949-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2949-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2949-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2949-117">See also</span></span>

- [<span data-ttu-id="d2949-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2949-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="d2949-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2949-119">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
