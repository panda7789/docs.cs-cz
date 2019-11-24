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
ms.openlocfilehash: 48c38288e960ff2e1fe21f30b6eceae8eeaac2da
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434851"
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="3c5fb-102">IMetaDataTables::GetTableIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="3c5fb-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="3c5fb-103">Gets the index for the table referenced by the specified token.</span><span class="sxs-lookup"><span data-stu-id="3c5fb-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c5fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c5fb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c5fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c5fb-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="3c5fb-106">[in] The token that references the table.</span><span class="sxs-lookup"><span data-stu-id="3c5fb-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="3c5fb-107">[out] A pointer to the returned index for the referenced table.</span><span class="sxs-lookup"><span data-stu-id="3c5fb-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c5fb-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3c5fb-108">Remarks</span></span>  
 <span data-ttu-id="3c5fb-109">We do not recommend the use of this method, because it does not return consistent results.</span><span class="sxs-lookup"><span data-stu-id="3c5fb-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="3c5fb-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span><span class="sxs-lookup"><span data-stu-id="3c5fb-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="3c5fb-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span><span class="sxs-lookup"><span data-stu-id="3c5fb-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c5fb-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3c5fb-112">Requirements</span></span>  
 <span data-ttu-id="3c5fb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c5fb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c5fb-114">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3c5fb-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3c5fb-115">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3c5fb-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3c5fb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c5fb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c5fb-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c5fb-117">See also</span></span>

- [<span data-ttu-id="3c5fb-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c5fb-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="3c5fb-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c5fb-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
