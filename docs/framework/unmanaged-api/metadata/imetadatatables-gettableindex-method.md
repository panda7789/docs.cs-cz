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
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="38e1e-102">IMetaDataTables::GetTableIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="38e1e-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="38e1e-103">Získá index pro tabulku, na kterou odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="38e1e-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38e1e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38e1e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38e1e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38e1e-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="38e1e-106">pro Token, který odkazuje na tabulku.</span><span class="sxs-lookup"><span data-stu-id="38e1e-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="38e1e-107">mimo Ukazatel na vrácený index odkazované tabulky.</span><span class="sxs-lookup"><span data-stu-id="38e1e-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38e1e-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="38e1e-108">Remarks</span></span>  
 <span data-ttu-id="38e1e-109">Nedoporučujeme používat tuto metodu, protože nevrací konzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="38e1e-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="38e1e-110">Informace o tabulce identifikátorů GUID najdete v dokumentaci k Common Language Infrastructure (CLI), zejména v oddílu oddíl II: definice metadat a sémantika.</span><span class="sxs-lookup"><span data-stu-id="38e1e-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="38e1e-111">Dokumentace je k dispozici online; v [tématu C# ECMA a Common Language Infrastructure](https://go.microsoft.com/fwlink/?LinkID=99212) Standards na webu MSDN a na [Standard ECMA-335-Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) se na webu ECMA International.</span><span class="sxs-lookup"><span data-stu-id="38e1e-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38e1e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="38e1e-112">Requirements</span></span>  
 <span data-ttu-id="38e1e-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38e1e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38e1e-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="38e1e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="38e1e-115">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="38e1e-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="38e1e-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38e1e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38e1e-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38e1e-117">See also</span></span>

- [<span data-ttu-id="38e1e-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="38e1e-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="38e1e-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="38e1e-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
