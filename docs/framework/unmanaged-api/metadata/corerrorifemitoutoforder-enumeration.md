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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 628ca1b555d80319312450d784981cfed1bda947
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045991"
---
# <a name="corerrorifemitoutoforder-enumeration"></a><span data-ttu-id="afceb-102">CorErrorIfEmitOutOfOrder – výčet</span><span class="sxs-lookup"><span data-stu-id="afceb-102">CorErrorIfEmitOutOfOrder Enumeration</span></span>
<span data-ttu-id="afceb-103">Obsahuje příznak hodnoty, které určují podmínky, za kterých by měl být vygenerován chybovou zprávu, když metadat je vygenerován mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="afceb-103">Contains flag values that indicate the conditions under which an error message should be generated when metadata is emitted out of order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afceb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afceb-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="afceb-105">Členové</span><span class="sxs-lookup"><span data-stu-id="afceb-105">Members</span></span>  
  
|<span data-ttu-id="afceb-106">Člen</span><span class="sxs-lookup"><span data-stu-id="afceb-106">Member</span></span>|<span data-ttu-id="afceb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="afceb-107">Description</span></span>|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|<span data-ttu-id="afceb-108">Určuje výchozí chování, které nejsou generovány chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="afceb-108">Indicates the default behavior, which does not generate error messages.</span></span>|  
|`MDErrorOutOfOrderNone`|<span data-ttu-id="afceb-109">Označuje, že kompilátor by neměl generovat chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="afceb-109">Indicates that the compiler should not generate error messages.</span></span>|  
|`MDErrorOutOfOrderAll`|<span data-ttu-id="afceb-110">Označuje, že by měl kompilátor generovat chybovou zprávu, když pole, vlastnosti, události, metody nebo parametr je vygenerován mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="afceb-110">Indicates that the compiler should generate an error message when a field, property, event, method, or parameter is emitted out of order.</span></span>|  
|`MDMethodOutOfOrder`|<span data-ttu-id="afceb-111">Označuje, že kompilátor by měl generovat chybovou zprávu, když metoda je vygenerován mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="afceb-111">Indicates that the compiler should generate an error message when a method is emitted out of order.</span></span>|  
|`MDFieldOutOfOrder`|<span data-ttu-id="afceb-112">Označuje, že by měl kompilátor generovat chybovou zprávu, když pole je vygenerován mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="afceb-112">Indicates that the compiler should generate an error message when a field is emitted out of order.</span></span>|  
|`MDParamOutOfOrder`|<span data-ttu-id="afceb-113">Označuje, že by měl kompilátor generovat chybovou zprávu, pokud parametr je vygenerován mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="afceb-113">Indicates that the compiler should generate an error message when a parameter is emitted out of order.</span></span>|  
|`MDPropertyOutOfOrder`|<span data-ttu-id="afceb-114">Označuje, že by měl kompilátor generovat chybovou zprávu, když vlastnost je vygenerován mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="afceb-114">Indicates that the compiler should generate an error message when a property is emitted out of order.</span></span>|  
|`MDEventOutOfOrder`|<span data-ttu-id="afceb-115">Označuje, že by měl kompilátor generovat chybovou zprávu při události je vygenerován mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="afceb-115">Indicates that the compiler should generate an error message when an event is emitted out of order.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="afceb-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="afceb-116">Requirements</span></span>  
 <span data-ttu-id="afceb-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afceb-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afceb-118">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="afceb-118">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="afceb-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afceb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afceb-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="afceb-120">See also</span></span>

- [<span data-ttu-id="afceb-121">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="afceb-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
