---
title: CorErrorIfEmitOutOfOrder – výčet
ms.date: 03/30/2017
api_name:
- CorErrorIfEmitOutOfOrder
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorErrorIfEmitOutOfOrder
helpviewer_keywords:
- CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type:
- apiref
ms.openlocfilehash: 57460ba30a8ce974b5ca89f76796c4dcf49ffecf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443583"
---
# <a name="corerrorifemitoutoforder-enumeration"></a><span data-ttu-id="14759-102">CorErrorIfEmitOutOfOrder – výčet</span><span class="sxs-lookup"><span data-stu-id="14759-102">CorErrorIfEmitOutOfOrder Enumeration</span></span>
<span data-ttu-id="14759-103">Obsahuje hodnoty příznaků, které určují podmínky, za kterých by se měla generovat chybová zpráva při vygenerování metadat mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="14759-103">Contains flag values that indicate the conditions under which an error message should be generated when metadata is emitted out of order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14759-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14759-104">Syntax</span></span>  
  
```cpp  
typedef enum CorErrorIfEmitOutOfOrder {  
  
    MDErrorOutOfOrderDefault    = 0x00000000,  
    MDErrorOutOfOrderNone       = 0x00000000,  
    MDErrorOutOfOrderAll        = 0xffffffff,  
    MDMethodOutOfOrder          = 0x00000001,  
    MDFieldOutOfOrder           = 0x00000002,  
    MDParamOutOfOrder           = 0x00000004,  
    MDPropertyOutOfOrder        = 0x00000008,  
    MDEventOutOfOrder           = 0x00000010  
  
} CorErrorIfEmitOutOfOrder;  
```  
  
## <a name="members"></a><span data-ttu-id="14759-105">Členové</span><span class="sxs-lookup"><span data-stu-id="14759-105">Members</span></span>  
  
|<span data-ttu-id="14759-106">Člen</span><span class="sxs-lookup"><span data-stu-id="14759-106">Member</span></span>|<span data-ttu-id="14759-107">Popis</span><span class="sxs-lookup"><span data-stu-id="14759-107">Description</span></span>|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|<span data-ttu-id="14759-108">Označuje výchozí chování, které negeneruje chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="14759-108">Indicates the default behavior, which does not generate error messages.</span></span>|  
|`MDErrorOutOfOrderNone`|<span data-ttu-id="14759-109">Označuje, že by kompilátor neměl generovat chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="14759-109">Indicates that the compiler should not generate error messages.</span></span>|  
|`MDErrorOutOfOrderAll`|<span data-ttu-id="14759-110">Určuje, že má kompilátor generovat chybovou zprávu, pokud je vygenerováno pole, vlastnost, událost, metoda nebo parametr.</span><span class="sxs-lookup"><span data-stu-id="14759-110">Indicates that the compiler should generate an error message when a field, property, event, method, or parameter is emitted out of order.</span></span>|  
|`MDMethodOutOfOrder`|<span data-ttu-id="14759-111">Označuje, že by kompilátor měl generovat chybovou zprávu, pokud je vygenerována metoda mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="14759-111">Indicates that the compiler should generate an error message when a method is emitted out of order.</span></span>|  
|`MDFieldOutOfOrder`|<span data-ttu-id="14759-112">Označuje, že by kompilátor měl generovat chybovou zprávu, pokud je vygenerováno pole mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="14759-112">Indicates that the compiler should generate an error message when a field is emitted out of order.</span></span>|  
|`MDParamOutOfOrder`|<span data-ttu-id="14759-113">Určuje, že má kompilátor vygenerovat chybovou zprávu, pokud je vygenerována chyba v příkazu.</span><span class="sxs-lookup"><span data-stu-id="14759-113">Indicates that the compiler should generate an error message when a parameter is emitted out of order.</span></span>|  
|`MDPropertyOutOfOrder`|<span data-ttu-id="14759-114">Označuje, že by kompilátor měl generovat chybovou zprávu, pokud je vygenerována vlastnost mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="14759-114">Indicates that the compiler should generate an error message when a property is emitted out of order.</span></span>|  
|`MDEventOutOfOrder`|<span data-ttu-id="14759-115">Určuje, že má kompilátor generovat chybovou zprávu, pokud je vyvolána událost mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="14759-115">Indicates that the compiler should generate an error message when an event is emitted out of order.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="14759-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14759-116">Requirements</span></span>  
 <span data-ttu-id="14759-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14759-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14759-118">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="14759-118">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="14759-119">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14759-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14759-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14759-120">See also</span></span>

- [<span data-ttu-id="14759-121">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="14759-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
