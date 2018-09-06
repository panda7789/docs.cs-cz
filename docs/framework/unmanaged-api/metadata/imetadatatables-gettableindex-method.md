---
title: IMetaDataTables::GetTableIndex – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableIndex
helpviewer_keywords:
- GetTableIndex method [.NET Framework metadata]
- IMetaDataTables::GetTableIndex method [.NET Framework metadata]
ms.assetid: c6ec3800-e0d9-4387-afb8-ddc0b818114c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f86fd424b397859dd70e113f2d8b8dcae7226f53
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44041064"
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="4676a-102">IMetaDataTables::GetTableIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="4676a-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="4676a-103">Získá index pro tabulku odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="4676a-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4676a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4676a-104">Syntax</span></span>  
  
```  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4676a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4676a-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="4676a-106">[in] Token, který odkazuje tabulku.</span><span class="sxs-lookup"><span data-stu-id="4676a-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="4676a-107">[out] Ukazatel na vrácené index pro odkazovanou tabulku.</span><span class="sxs-lookup"><span data-stu-id="4676a-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4676a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4676a-108">Remarks</span></span>  
 <span data-ttu-id="4676a-109">Nedoporučujeme použití této metody, protože nevrací konzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="4676a-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="4676a-110">Informace o tabulce GUID najdete v dokumentaci společné jazykové infrastruktury (CLI), zejména "oddíl II: Metadata definice a sémantika".</span><span class="sxs-lookup"><span data-stu-id="4676a-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="4676a-111">Dokumentace je k dispozici online; Zobrazit [ECMA C# a společné normy jazykové infrastruktury](https://go.microsoft.com/fwlink/?LinkID=99212) na webu MSDN a [Standard ECMA-335 – společné jazykové infrastruktury (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) na webu Ecma International.</span><span class="sxs-lookup"><span data-stu-id="4676a-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4676a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4676a-112">Requirements</span></span>  
 <span data-ttu-id="4676a-113">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4676a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4676a-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4676a-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4676a-115">**Knihovna:** použit jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4676a-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4676a-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4676a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4676a-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="4676a-117">See Also</span></span>  
 [<span data-ttu-id="4676a-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4676a-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="4676a-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4676a-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
