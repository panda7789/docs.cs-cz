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
ms.openlocfilehash: 5e88dd0053ec7562d6223c18479f4a4fadc68c12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701791"
---
# <a name="ceesectionattr-enumeration"></a><span data-ttu-id="7d75a-102">CeeSectionAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="7d75a-102">CeeSectionAttr Enumeration</span></span>
<span data-ttu-id="7d75a-103">Obsahuje hodnoty, které určují atributy oddílu pro použití [iceegen –](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7d75a-103">Provides values that specify attributes of a section for use by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d75a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d75a-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="7d75a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="7d75a-105">Members</span></span>  
  
|<span data-ttu-id="7d75a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="7d75a-106">Member</span></span>|<span data-ttu-id="7d75a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7d75a-107">Description</span></span>|  
|------------|-----------------|  
|`sdNone`|<span data-ttu-id="7d75a-108">Oddíl nemá žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="7d75a-108">Section has no attributes.</span></span>|  
|`sdReadOnly`|<span data-ttu-id="7d75a-109">Oddíl obsahuje inicializovaná data, která lze pouze číst, nejsou aktualizována.</span><span class="sxs-lookup"><span data-stu-id="7d75a-109">Section contains initialized data that can be only read, not updated.</span></span>|  
|`sdReadWrite`|<span data-ttu-id="7d75a-110">Oddíl obsahuje inicializovaná data, která může číst nebo aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="7d75a-110">Section contains initialized data that can be read or updated.</span></span>|  
|`sdExecute`|<span data-ttu-id="7d75a-111">Oddíl obsahuje spustitelný kód, který může číst a spustit.</span><span class="sxs-lookup"><span data-stu-id="7d75a-111">Section contains executable code that is allowed to be read and executed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7d75a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d75a-112">Requirements</span></span>  
 <span data-ttu-id="7d75a-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d75a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d75a-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7d75a-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7d75a-115">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7d75a-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7d75a-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d75a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d75a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d75a-117">See also</span></span>
- [<span data-ttu-id="7d75a-118">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="7d75a-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
