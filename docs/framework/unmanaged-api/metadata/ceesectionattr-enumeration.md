---
title: CeeSectionAttr – výčet
ms.date: 03/30/2017
api_name:
- CeeSectionAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionAttr
helpviewer_keywords:
- CeeSectionAttr enumeration [.NET Framework metadata]
ms.assetid: 0db51881-b869-4677-a715-1726a9216489
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c317524cefd7ed654e76bdd7051cdcd7653062db
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101787"
---
# <a name="ceesectionattr-enumeration"></a><span data-ttu-id="ccf6c-102">CeeSectionAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="ccf6c-102">CeeSectionAttr Enumeration</span></span>
<span data-ttu-id="ccf6c-103">Obsahuje hodnoty, které určují atributy oddílu pro použití [iceegen –](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ccf6c-103">Provides values that specify attributes of a section for use by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccf6c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccf6c-104">Syntax</span></span>  
  
```  
typedef enum  {  
    sdNone      = 0,  
    sdReadOnly  = IMAGE_SCN_CNT_INITIALIZED_DATA |  
                  IMAGE_SCN_MEM_READ,  
    sdReadWrite = sdReadOnly | IMAGE_SCN_MEM_WRITE,  
    sdExecute   = IMAGE_SCN_MEM_READ | IMAGE_SCN_CNT_CODE |  
                  IMAGE_SCN_MEM_EXECUTE  
} CeeSectionAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="ccf6c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ccf6c-105">Members</span></span>  
  
|<span data-ttu-id="ccf6c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="ccf6c-106">Member</span></span>|<span data-ttu-id="ccf6c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ccf6c-107">Description</span></span>|  
|------------|-----------------|  
|`sdNone`|<span data-ttu-id="ccf6c-108">Oddíl nemá žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="ccf6c-108">Section has no attributes.</span></span>|  
|`sdReadOnly`|<span data-ttu-id="ccf6c-109">Oddíl obsahuje inicializovaná data, která lze pouze číst, nejsou aktualizována.</span><span class="sxs-lookup"><span data-stu-id="ccf6c-109">Section contains initialized data that can be only read, not updated.</span></span>|  
|`sdReadWrite`|<span data-ttu-id="ccf6c-110">Oddíl obsahuje inicializovaná data, která může číst nebo aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="ccf6c-110">Section contains initialized data that can be read or updated.</span></span>|  
|`sdExecute`|<span data-ttu-id="ccf6c-111">Oddíl obsahuje spustitelný kód, který může číst a spustit.</span><span class="sxs-lookup"><span data-stu-id="ccf6c-111">Section contains executable code that is allowed to be read and executed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ccf6c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ccf6c-112">Requirements</span></span>  
 <span data-ttu-id="ccf6c-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccf6c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccf6c-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ccf6c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ccf6c-115">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ccf6c-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ccf6c-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccf6c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccf6c-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ccf6c-117">See also</span></span>

- [<span data-ttu-id="ccf6c-118">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="ccf6c-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
