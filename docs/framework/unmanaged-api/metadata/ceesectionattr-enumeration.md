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
ms.openlocfilehash: 6da8a111f716906e403d85bc0b1a29eba7238100
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006061"
---
# <a name="ceesectionattr-enumeration"></a><span data-ttu-id="7b738-102">CeeSectionAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="7b738-102">CeeSectionAttr Enumeration</span></span>
<span data-ttu-id="7b738-103">Poskytuje hodnoty, které určují atributy oddílu pro použití rozhraní [ICeeGen](iceegen-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="7b738-103">Provides values that specify attributes of a section for use by the [ICeeGen](iceegen-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b738-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b738-104">Syntax</span></span>  
  
```cpp  
typedef enum  {  
    sdNone      = 0,  
    sdReadOnly  = IMAGE_SCN_CNT_INITIALIZED_DATA |  
                  IMAGE_SCN_MEM_READ,  
    sdReadWrite = sdReadOnly | IMAGE_SCN_MEM_WRITE,  
    sdExecute   = IMAGE_SCN_MEM_READ | IMAGE_SCN_CNT_CODE |  
                  IMAGE_SCN_MEM_EXECUTE  
} CeeSectionAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="7b738-105">Členové</span><span class="sxs-lookup"><span data-stu-id="7b738-105">Members</span></span>  
  
|<span data-ttu-id="7b738-106">Člen</span><span class="sxs-lookup"><span data-stu-id="7b738-106">Member</span></span>|<span data-ttu-id="7b738-107">Description</span><span class="sxs-lookup"><span data-stu-id="7b738-107">Description</span></span>|  
|------------|-----------------|  
|`sdNone`|<span data-ttu-id="7b738-108">Oddíl nemá žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="7b738-108">Section has no attributes.</span></span>|  
|`sdReadOnly`|<span data-ttu-id="7b738-109">Oddíl obsahuje inicializovaná data, která je možné číst, nikoli aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="7b738-109">Section contains initialized data that can be only read, not updated.</span></span>|  
|`sdReadWrite`|<span data-ttu-id="7b738-110">Oddíl obsahuje inicializovaná data, která je možné číst nebo aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="7b738-110">Section contains initialized data that can be read or updated.</span></span>|  
|`sdExecute`|<span data-ttu-id="7b738-111">Oddíl obsahuje spustitelný kód, který může být načten a proveden.</span><span class="sxs-lookup"><span data-stu-id="7b738-111">Section contains executable code that is allowed to be read and executed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7b738-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b738-112">Requirements</span></span>  
 <span data-ttu-id="7b738-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b738-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b738-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7b738-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7b738-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7b738-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7b738-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b738-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b738-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b738-117">See also</span></span>

- [<span data-ttu-id="7b738-118">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="7b738-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
