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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 872f5a9eaa17a777cfbb14fea34cc80e0b7c04ad
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487479"
---
# <a name="imetadatatablesgetnextguid-method"></a><span data-ttu-id="3b791-102">IMetaDataTables::GetNextGuid – metoda</span><span class="sxs-lookup"><span data-stu-id="3b791-102">IMetaDataTables::GetNextGuid Method</span></span>
<span data-ttu-id="3b791-103">Získá index další hodnota identifikátoru GUID v aktuálním sloupci tabulky.</span><span class="sxs-lookup"><span data-stu-id="3b791-103">Gets the index of the next GUID value in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b791-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b791-104">Syntax</span></span>  
  
```  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b791-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3b791-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="3b791-106">[in] Hodnota indexu ze sloupce tabulky identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="3b791-106">[in] The index value from a GUID table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="3b791-107">[out] Ukazatel na index další hodnota identifikátoru GUID.</span><span class="sxs-lookup"><span data-stu-id="3b791-107">[out] A pointer to the index of the next GUID value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b791-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3b791-108">Remarks</span></span>  
 <span data-ttu-id="3b791-109">Nedoporučujeme použití této metody, protože nevrací konzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="3b791-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="3b791-110">Informace o tabulce GUID najdete v dokumentaci společné jazykové infrastruktury (CLI), zejména "oddíl II: Definice metadat a sémantika".</span><span class="sxs-lookup"><span data-stu-id="3b791-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="3b791-111">Dokumentace je k dispozici online; Zobrazit [ECMA C# a společné normy jazykové infrastruktury](https://go.microsoft.com/fwlink/?LinkID=99212) na webu MSDN a [Standard ECMA-335 – společné jazykové infrastruktury (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) na webu Ecma International.</span><span class="sxs-lookup"><span data-stu-id="3b791-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b791-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3b791-112">Requirements</span></span>  
 <span data-ttu-id="3b791-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b791-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b791-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3b791-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3b791-115">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3b791-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3b791-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b791-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b791-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b791-117">See also</span></span>
- [<span data-ttu-id="3b791-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3b791-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="3b791-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3b791-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
