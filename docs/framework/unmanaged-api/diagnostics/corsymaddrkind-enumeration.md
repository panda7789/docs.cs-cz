---
title: "CorSymAddrKind – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSymAddrKind
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSymAddrKind
helpviewer_keywords: CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 300913f9ea89044e425f9f05856d13fa15cdc015
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corsymaddrkind-enumeration"></a><span data-ttu-id="4ae05-102">CorSymAddrKind – výčet</span><span class="sxs-lookup"><span data-stu-id="4ae05-102">CorSymAddrKind Enumeration</span></span>
<span data-ttu-id="4ae05-103">Určuje typ adresa paměti.</span><span class="sxs-lookup"><span data-stu-id="4ae05-103">Indicates the type of memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ae05-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ae05-104">Syntax</span></span>  
  
```  
typedef enum CorSymAddrKind  
{  
    ADDR_IL_OFFSET          = 1,  
    ADDR_NATIVE_RVA         = 2,  
    ADDR_NATIVE_REGISTER    = 3,  
    ADDR_NATIVE_REGREL      = 4,  
    ADDR_NATIVE_OFFSET      = 5,  
    ADDR_NATIVE_REGREG      = 6,  
    ADDR_NATIVE_REGSTK      = 7,  
    ADDR_NATIVE_STKREG      = 8,  
    ADDR_BITFIELD           = 9,  
    ADDR_NATIVE_ISECTOFFSET = 10  
} CorSymAddrKind;  
```  
  
## <a name="members"></a><span data-ttu-id="4ae05-105">Členové</span><span class="sxs-lookup"><span data-stu-id="4ae05-105">Members</span></span>  
  
|<span data-ttu-id="4ae05-106">Člen</span><span class="sxs-lookup"><span data-stu-id="4ae05-106">Member</span></span>|<span data-ttu-id="4ae05-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4ae05-107">Description</span></span>|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|<span data-ttu-id="4ae05-108">Označuje Microsoft (MSIL intermediate language) místní proměnné nebo parametru indexem.</span><span class="sxs-lookup"><span data-stu-id="4ae05-108">Indicates a Microsoft intermediate language (MSIL) local variable or parameter index.</span></span>|  
|`ADDR_NATIVE_RVA`|<span data-ttu-id="4ae05-109">Určuje relativní virtuální adresy do modulu.</span><span class="sxs-lookup"><span data-stu-id="4ae05-109">Indicates a relative virtual address into a module.</span></span>|  
|`ADDR_NATIVE_REGISTER`|<span data-ttu-id="4ae05-110">Označuje registrace procesoru.</span><span class="sxs-lookup"><span data-stu-id="4ae05-110">Indicates a CPU register.</span></span>|  
|`ADDR_NATIVE_REGREL`|<span data-ttu-id="4ae05-111">Označuje, že první adresa je registr a druhá adresa je posun.</span><span class="sxs-lookup"><span data-stu-id="4ae05-111">Indicates that the first address is a register and the second address is an offset.</span></span>|  
|`ADDR_NATIVE_OFFSET`|<span data-ttu-id="4ae05-112">Určuje posun z bázové adresy.</span><span class="sxs-lookup"><span data-stu-id="4ae05-112">Indicates an offset from a base address.</span></span>|  
|`ADDR_NATIVE_REGREG`|<span data-ttu-id="4ae05-113">Označuje, že první adresa je nízkou část do registru a druhá adresa je vysoká část.</span><span class="sxs-lookup"><span data-stu-id="4ae05-113">Indicates that the first address is the low portion of a register, and the second address is the high portion.</span></span>|  
|`ADDR_NATIVE_REGSTK`|<span data-ttu-id="4ae05-114">Označuje, že první adresa je nízkou část zaregistrovat, druhý je vysoká část a třetí je posun.</span><span class="sxs-lookup"><span data-stu-id="4ae05-114">Indicates that the first address is the low portion of a register, the second is the high portion, and the third is an offset.</span></span>|  
|`ADDR_NATIVE_STKREG`|<span data-ttu-id="4ae05-115">Označuje, že první adresa je registr, posun je druhý a třetí je vysoká část registru.</span><span class="sxs-lookup"><span data-stu-id="4ae05-115">Indicates that the first address is a register, the second is an offset, and the third is the high portion of the register.</span></span>|  
|`ADDR_BITFIELD`|<span data-ttu-id="4ae05-116">Označuje, že první adresa je začátek pole a druhá adresa je délka pole.</span><span class="sxs-lookup"><span data-stu-id="4ae05-116">Indicates that the first address is the start of a field and the second address is the field length.</span></span>|  
|`ADDR_NATIVE_ISECTOFFSET`|<span data-ttu-id="4ae05-117">Označuje, že první adresa je v části a druhá adresa je posun.</span><span class="sxs-lookup"><span data-stu-id="4ae05-117">Indicates that the first address is the section and the second address is an offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4ae05-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4ae05-118">Requirements</span></span>  
 <span data-ttu-id="4ae05-119">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4ae05-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ae05-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ae05-120">See Also</span></span>  
 [<span data-ttu-id="4ae05-121">Výčty pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="4ae05-121">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
