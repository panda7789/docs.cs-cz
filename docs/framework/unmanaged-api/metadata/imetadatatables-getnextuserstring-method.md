---
title: "IMetaDataTables::GetNextUserString – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetNextUserString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetNextUserString
helpviewer_keywords:
- GetNextUserString method [.NET Framework metadata]
- IMetaDataTables::GetNextUserString method [.NET Framework metadata]
ms.assetid: b7cb40ee-67b7-4f4e-8dcc-ee7ac8bc986b
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 318bd7d05a7da5ce728ca80fe9bacfd84f501884
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="993d4-102">IMetaDataTables::GetNextUserString – metoda</span><span class="sxs-lookup"><span data-stu-id="993d4-102">IMetaDataTables::GetNextUserString Method</span></span>
<span data-ttu-id="993d4-103">Získá index řádku, který obsahuje další pevně řetězce v aktuálním sloupec tabulky.</span><span class="sxs-lookup"><span data-stu-id="993d4-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="993d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="993d4-104">Syntax</span></span>  
  
```  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="993d4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="993d4-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="993d4-106">[v] Hodnota indexu z aktuální sloupec řetězec.</span><span class="sxs-lookup"><span data-stu-id="993d4-106">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="993d4-107">[out] Ukazatel na index řádku další řetězce ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="993d4-107">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="993d4-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="993d4-108">Remarks</span></span>  
 <span data-ttu-id="993d4-109">Nedoporučujeme použití této metody, protože nevrací konzistentních výsledků.</span><span class="sxs-lookup"><span data-stu-id="993d4-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="993d4-110">Informace o tabulce GUID najdete v dokumentaci společné jazykové infrastruktury (CLI), zejména "oddílu II: Metadata definice a sémantiku".</span><span class="sxs-lookup"><span data-stu-id="993d4-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="993d4-111">Dokumentace je k dispozici online; v tématu [ECMA C# a společné jazykové infrastruktury normy](http://go.microsoft.com/fwlink/?LinkID=99212) na webu MSDN a [standardní standardy ECMA-335 - společné jazykové infrastruktury (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) na webu Ecma mezinárodní.</span><span class="sxs-lookup"><span data-stu-id="993d4-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="993d4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="993d4-112">Requirements</span></span>  
 <span data-ttu-id="993d4-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="993d4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="993d4-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="993d4-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="993d4-115">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="993d4-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="993d4-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="993d4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="993d4-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="993d4-117">See Also</span></span>  
 [<span data-ttu-id="993d4-118">Imetadatatables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="993d4-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="993d4-119">Imetadatatables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="993d4-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
