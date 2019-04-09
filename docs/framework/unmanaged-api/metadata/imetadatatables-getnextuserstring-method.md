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
ms.openlocfilehash: 3ce6cfd6a331c9d9695f65eb3a670305de38d010
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191171"
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="9ce37-102">IMetaDataTables::GetNextUserString – metoda</span><span class="sxs-lookup"><span data-stu-id="9ce37-102">IMetaDataTables::GetNextUserString Method</span></span>
<span data-ttu-id="9ce37-103">Získá index řádku, který obsahuje další pevně zakódované řetězce v aktuálním sloupci tabulky.</span><span class="sxs-lookup"><span data-stu-id="9ce37-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ce37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ce37-104">Syntax</span></span>  
  
```  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ce37-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ce37-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="9ce37-106">[in] Hodnota indexu z aktuální řetězcový sloupec.</span><span class="sxs-lookup"><span data-stu-id="9ce37-106">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="9ce37-107">[out] Ukazatel na index řádku další řetězce ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="9ce37-107">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ce37-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ce37-108">Remarks</span></span>  
 <span data-ttu-id="9ce37-109">Nedoporučujeme použití této metody, protože nevrací konzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="9ce37-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="9ce37-110">Informace o tabulce GUID najdete v dokumentaci společné jazykové infrastruktury (CLI), zejména "oddíl II: Definice metadat a sémantika".</span><span class="sxs-lookup"><span data-stu-id="9ce37-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="9ce37-111">Dokumentace je k dispozici online; Zobrazit [ECMA C# a společné normy jazykové infrastruktury](https://go.microsoft.com/fwlink/?LinkID=99212) na webu MSDN a [Standard ECMA-335 – společné jazykové infrastruktury (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) na webu Ecma International.</span><span class="sxs-lookup"><span data-stu-id="9ce37-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ce37-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ce37-112">Requirements</span></span>  
 <span data-ttu-id="9ce37-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ce37-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ce37-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9ce37-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9ce37-115">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9ce37-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="9ce37-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9ce37-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9ce37-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ce37-117">See also</span></span>

- [<span data-ttu-id="9ce37-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ce37-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="9ce37-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ce37-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
