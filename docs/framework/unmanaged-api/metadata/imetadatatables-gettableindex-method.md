---
title: "IMetaDataTables::GetTableIndex – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetTableIndex
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetTableIndex
helpviewer_keywords:
- GetTableIndex method [.NET Framework metadata]
- IMetaDataTables::GetTableIndex method [.NET Framework metadata]
ms.assetid: c6ec3800-e0d9-4387-afb8-ddc0b818114c
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d49e1258011d68a6278d1c40500386024a2cb0d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="9bd4b-102">IMetaDataTables::GetTableIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="9bd4b-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="9bd4b-103">Získá index pro tabulku odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bd4b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9bd4b-104">Syntax</span></span>  
  
```  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9bd4b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9bd4b-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="9bd4b-106">[v] Token, který odkazuje tabulku.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="9bd4b-107">[out] Ukazatel na vrácený index pro odkazovanou tabulku.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bd4b-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9bd4b-108">Remarks</span></span>  
 <span data-ttu-id="9bd4b-109">Nedoporučujeme použití této metody, protože nevrací konzistentních výsledků.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="9bd4b-110">Informace o tabulce GUID najdete v dokumentaci společné jazykové infrastruktury (CLI), zejména "oddílu II: Metadata definice a sémantiku".</span><span class="sxs-lookup"><span data-stu-id="9bd4b-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="9bd4b-111">Dokumentace je k dispozici online; v tématu [ECMA C# a společné jazykové infrastruktury normy](http://go.microsoft.com/fwlink/?LinkID=99212) na webu MSDN a [standardní standardy ECMA-335 - společné jazykové infrastruktury (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) na webu Ecma mezinárodní.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bd4b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9bd4b-112">Requirements</span></span>  
 <span data-ttu-id="9bd4b-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bd4b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bd4b-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9bd4b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9bd4b-115">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9bd4b-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9bd4b-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bd4b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bd4b-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="9bd4b-117">See Also</span></span>  
 [<span data-ttu-id="9bd4b-118">Imetadatatables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9bd4b-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="9bd4b-119">Imetadatatables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9bd4b-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
