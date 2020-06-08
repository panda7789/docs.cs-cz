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
ms.openlocfilehash: 3638ab12fc311ece9f24608cbb36219e10f01f2d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501162"
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="81419-102">IMetaDataTables::GetTableIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="81419-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="81419-103">Získá index pro tabulku, na kterou odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="81419-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81419-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81419-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81419-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81419-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="81419-106">pro Token, který odkazuje na tabulku.</span><span class="sxs-lookup"><span data-stu-id="81419-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="81419-107">mimo Ukazatel na vrácený index odkazované tabulky.</span><span class="sxs-lookup"><span data-stu-id="81419-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81419-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81419-108">Remarks</span></span>  
 <span data-ttu-id="81419-109">Nedoporučujeme používat tuto metodu, protože nevrací konzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="81419-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="81419-110">Informace o tabulce identifikátorů GUID najdete v dokumentaci k Common Language Infrastructure (CLI), zejména v oddílu oddíl II: definice metadat a sémantika.</span><span class="sxs-lookup"><span data-stu-id="81419-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="81419-111">Dokumentace je k dispozici online; viz [ECMA C# a Common Language Infrastructure standardy](../../../standard/components.md#applicable-standards) a [standardní ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="81419-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81419-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="81419-112">Requirements</span></span>  
 <span data-ttu-id="81419-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81419-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81419-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="81419-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="81419-115">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="81419-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="81419-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81419-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81419-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81419-117">See also</span></span>

- [<span data-ttu-id="81419-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="81419-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="81419-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="81419-119">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
