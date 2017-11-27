---
title: "CorErrorIfEmitOutOfOrder – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorErrorIfEmitOutOfOrder
api_location: mscoree.dll
api_type: COM
f1_keywords: CorErrorIfEmitOutOfOrder
helpviewer_keywords: CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d2cf80375622912c6bb9a59696f37aed2d594253
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="corerrorifemitoutoforder-enumeration"></a><span data-ttu-id="a01d1-102">CorErrorIfEmitOutOfOrder – výčet</span><span class="sxs-lookup"><span data-stu-id="a01d1-102">CorErrorIfEmitOutOfOrder Enumeration</span></span>
<span data-ttu-id="a01d1-103">Obsahuje příznak hodnoty, které označují podmínky, za kterých by měl být vygenerován chybovou zprávu, když metadata jsou vydávány mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="a01d1-103">Contains flag values that indicate the conditions under which an error message should be generated when metadata is emitted out of order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a01d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a01d1-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="a01d1-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a01d1-105">Members</span></span>  
  
|<span data-ttu-id="a01d1-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a01d1-106">Member</span></span>|<span data-ttu-id="a01d1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a01d1-107">Description</span></span>|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|<span data-ttu-id="a01d1-108">Určuje výchozí chování, který negeneruje chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="a01d1-108">Indicates the default behavior, which does not generate error messages.</span></span>|  
|`MDErrorOutOfOrderNone`|<span data-ttu-id="a01d1-109">Označuje, že kompilátor by neměla generovat chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="a01d1-109">Indicates that the compiler should not generate error messages.</span></span>|  
|`MDErrorOutOfOrderAll`|<span data-ttu-id="a01d1-110">Označuje, že kompilátor by měl generovat chybovou zprávu, pokud pole, vlastnost, události, metoda nebo parametr je vygenerované mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="a01d1-110">Indicates that the compiler should generate an error message when a field, property, event, method, or parameter is emitted out of order.</span></span>|  
|`MDMethodOutOfOrder`|<span data-ttu-id="a01d1-111">Označuje, že kompilátor by měl generovat chybovou zprávu, když metoda je vygenerované mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="a01d1-111">Indicates that the compiler should generate an error message when a method is emitted out of order.</span></span>|  
|`MDFieldOutOfOrder`|<span data-ttu-id="a01d1-112">Označuje, že kompilátor by měl generovat chybovou zprávu, pokud je pole vygenerované mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="a01d1-112">Indicates that the compiler should generate an error message when a field is emitted out of order.</span></span>|  
|`MDParamOutOfOrder`|<span data-ttu-id="a01d1-113">Označuje, že kompilátor by měl generovat chybovou zprávu, pokud je parametr vygenerované mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="a01d1-113">Indicates that the compiler should generate an error message when a parameter is emitted out of order.</span></span>|  
|`MDPropertyOutOfOrder`|<span data-ttu-id="a01d1-114">Označuje, že kompilátor by měl generovat chybovou zprávu, pokud je vlastnost vygenerované mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="a01d1-114">Indicates that the compiler should generate an error message when a property is emitted out of order.</span></span>|  
|`MDEventOutOfOrder`|<span data-ttu-id="a01d1-115">Označuje, že kompilátor by měl generovat chybovou zprávu, když je vygenerované událost mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="a01d1-115">Indicates that the compiler should generate an error message when an event is emitted out of order.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a01d1-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a01d1-116">Requirements</span></span>  
 <span data-ttu-id="a01d1-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a01d1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a01d1-118">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="a01d1-118">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a01d1-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a01d1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a01d1-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="a01d1-120">See Also</span></span>  
 [<span data-ttu-id="a01d1-121">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="a01d1-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
