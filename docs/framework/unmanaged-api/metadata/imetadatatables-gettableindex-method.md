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
ms.openlocfilehash: d3e056bc93c2faf2b1509536b8d8d4df6886dd20
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937384"
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="37701-102">IMetaDataTables::GetTableIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="37701-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="37701-103">Získá index pro tabulku, na kterou odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="37701-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37701-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37701-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37701-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="37701-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="37701-106">pro Token, který odkazuje na tabulku.</span><span class="sxs-lookup"><span data-stu-id="37701-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="37701-107">mimo Ukazatel na vrácený index odkazované tabulky.</span><span class="sxs-lookup"><span data-stu-id="37701-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37701-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37701-108">Remarks</span></span>  
 <span data-ttu-id="37701-109">Nedoporučujeme používat tuto metodu, protože nevrací konzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="37701-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="37701-110">Informace o tabulce identifikátorů GUID najdete v dokumentaci k Common Language Infrastructure (CLI), zejména v oddílu oddíl II: definice metadat a sémantika.</span><span class="sxs-lookup"><span data-stu-id="37701-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="37701-111">Dokumentace je k dispozici online; viz [ECMA C# a Common Language Infrastructure standardy](../../../standard/components.md#applicable-standards) a [standardní ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="37701-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37701-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37701-112">Requirements</span></span>  
 <span data-ttu-id="37701-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37701-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37701-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="37701-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="37701-115">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="37701-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="37701-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37701-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37701-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37701-117">See also</span></span>

- [<span data-ttu-id="37701-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37701-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="37701-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37701-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
