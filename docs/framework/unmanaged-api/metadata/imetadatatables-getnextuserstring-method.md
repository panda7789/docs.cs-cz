---
title: IMetaDataTables::GetNextUserString – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextUserString
helpviewer_keywords:
- GetNextUserString method [.NET Framework metadata]
- IMetaDataTables::GetNextUserString method [.NET Framework metadata]
ms.assetid: b7cb40ee-67b7-4f4e-8dcc-ee7ac8bc986b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 01b326765e792bf97658d951a2d5590d22eff546
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43735186"
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="ceb9d-102">IMetaDataTables::GetNextUserString – metoda</span><span class="sxs-lookup"><span data-stu-id="ceb9d-102">IMetaDataTables::GetNextUserString Method</span></span>
<span data-ttu-id="ceb9d-103">Získá index řádku, který obsahuje další pevně zakódované řetězce v aktuálním sloupci tabulky.</span><span class="sxs-lookup"><span data-stu-id="ceb9d-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceb9d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ceb9d-104">Syntax</span></span>  
  
```  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ceb9d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ceb9d-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="ceb9d-106">[in] Hodnota indexu z aktuální řetězcový sloupec.</span><span class="sxs-lookup"><span data-stu-id="ceb9d-106">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="ceb9d-107">[out] Ukazatel na index řádku další řetězce ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="ceb9d-107">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ceb9d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ceb9d-108">Remarks</span></span>  
 <span data-ttu-id="ceb9d-109">Nedoporučujeme použití této metody, protože nevrací konzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="ceb9d-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="ceb9d-110">Informace o tabulce GUID najdete v dokumentaci společné jazykové infrastruktury (CLI), zejména "oddíl II: Metadata definice a sémantika".</span><span class="sxs-lookup"><span data-stu-id="ceb9d-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="ceb9d-111">Dokumentace je k dispozici online; Zobrazit [ECMA C# a společné normy jazykové infrastruktury](https://go.microsoft.com/fwlink/?LinkID=99212) na webu MSDN a [Standard ECMA-335 – společné jazykové infrastruktury (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) na webu Ecma International.</span><span class="sxs-lookup"><span data-stu-id="ceb9d-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ceb9d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ceb9d-112">Requirements</span></span>  
 <span data-ttu-id="ceb9d-113">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ceb9d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ceb9d-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ceb9d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ceb9d-115">**Knihovna:** použit jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ceb9d-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ceb9d-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ceb9d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceb9d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="ceb9d-117">See Also</span></span>  
 [<span data-ttu-id="ceb9d-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ceb9d-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="ceb9d-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ceb9d-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
