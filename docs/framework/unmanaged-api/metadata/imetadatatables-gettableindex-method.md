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
ms.openlocfilehash: eebef02babdca5305deaa4ae11e4bca3bf8bf504
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154398"
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="f086f-102">IMetaDataTables::GetTableIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="f086f-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="f086f-103">Získá index pro tabulku odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="f086f-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f086f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f086f-104">Syntax</span></span>  
  
```  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f086f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f086f-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="f086f-106">[in] Token, který odkazuje tabulku.</span><span class="sxs-lookup"><span data-stu-id="f086f-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="f086f-107">[out] Ukazatel na vrácené index pro odkazovanou tabulku.</span><span class="sxs-lookup"><span data-stu-id="f086f-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f086f-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f086f-108">Remarks</span></span>  
 <span data-ttu-id="f086f-109">Nedoporučujeme použití této metody, protože nevrací konzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="f086f-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="f086f-110">Informace o tabulce GUID najdete v dokumentaci společné jazykové infrastruktury (CLI), zejména "oddíl II: Definice metadat a sémantika".</span><span class="sxs-lookup"><span data-stu-id="f086f-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="f086f-111">Dokumentace je k dispozici online; Zobrazit [ECMA C# a společné normy jazykové infrastruktury](https://go.microsoft.com/fwlink/?LinkID=99212) na webu MSDN a [Standard ECMA-335 – společné jazykové infrastruktury (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) na webu Ecma International.</span><span class="sxs-lookup"><span data-stu-id="f086f-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f086f-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f086f-112">Requirements</span></span>  
 <span data-ttu-id="f086f-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f086f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f086f-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f086f-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f086f-115">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f086f-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="f086f-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f086f-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f086f-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f086f-117">See also</span></span>

- [<span data-ttu-id="f086f-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f086f-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="f086f-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f086f-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
