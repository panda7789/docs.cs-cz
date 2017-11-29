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
ms.openlocfilehash: 56bb55d9c9f85ae8f8112f16dcf552295699826d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="corsymaddrkind-enumeration"></a><span data-ttu-id="d1536-102">CorSymAddrKind – výčet</span><span class="sxs-lookup"><span data-stu-id="d1536-102">CorSymAddrKind Enumeration</span></span>
<span data-ttu-id="d1536-103">Určuje typ adresa paměti.</span><span class="sxs-lookup"><span data-stu-id="d1536-103">Indicates the type of memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1536-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1536-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="d1536-105">Členové</span><span class="sxs-lookup"><span data-stu-id="d1536-105">Members</span></span>  
  
|<span data-ttu-id="d1536-106">Člen</span><span class="sxs-lookup"><span data-stu-id="d1536-106">Member</span></span>|<span data-ttu-id="d1536-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d1536-107">Description</span></span>|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|<span data-ttu-id="d1536-108">Označuje Microsoft (MSIL intermediate language) místní proměnné nebo parametru indexem.</span><span class="sxs-lookup"><span data-stu-id="d1536-108">Indicates a Microsoft intermediate language (MSIL) local variable or parameter index.</span></span>|  
|`ADDR_NATIVE_RVA`|<span data-ttu-id="d1536-109">Určuje relativní virtuální adresy do modulu.</span><span class="sxs-lookup"><span data-stu-id="d1536-109">Indicates a relative virtual address into a module.</span></span>|  
|`ADDR_NATIVE_REGISTER`|<span data-ttu-id="d1536-110">Označuje registrace procesoru.</span><span class="sxs-lookup"><span data-stu-id="d1536-110">Indicates a CPU register.</span></span>|  
|`ADDR_NATIVE_REGREL`|<span data-ttu-id="d1536-111">Označuje, že první adresa je registr a druhá adresa je posun.</span><span class="sxs-lookup"><span data-stu-id="d1536-111">Indicates that the first address is a register and the second address is an offset.</span></span>|  
|`ADDR_NATIVE_OFFSET`|<span data-ttu-id="d1536-112">Určuje posun z bázové adresy.</span><span class="sxs-lookup"><span data-stu-id="d1536-112">Indicates an offset from a base address.</span></span>|  
|`ADDR_NATIVE_REGREG`|<span data-ttu-id="d1536-113">Označuje, že první adresa je nízkou část do registru a druhá adresa je vysoká část.</span><span class="sxs-lookup"><span data-stu-id="d1536-113">Indicates that the first address is the low portion of a register, and the second address is the high portion.</span></span>|  
|`ADDR_NATIVE_REGSTK`|<span data-ttu-id="d1536-114">Označuje, že první adresa je nízkou část zaregistrovat, druhý je vysoká část a třetí je posun.</span><span class="sxs-lookup"><span data-stu-id="d1536-114">Indicates that the first address is the low portion of a register, the second is the high portion, and the third is an offset.</span></span>|  
|`ADDR_NATIVE_STKREG`|<span data-ttu-id="d1536-115">Označuje, že první adresa je registr, posun je druhý a třetí je vysoká část registru.</span><span class="sxs-lookup"><span data-stu-id="d1536-115">Indicates that the first address is a register, the second is an offset, and the third is the high portion of the register.</span></span>|  
|`ADDR_BITFIELD`|<span data-ttu-id="d1536-116">Označuje, že první adresa je začátek pole a druhá adresa je délka pole.</span><span class="sxs-lookup"><span data-stu-id="d1536-116">Indicates that the first address is the start of a field and the second address is the field length.</span></span>|  
|`ADDR_NATIVE_ISECTOFFSET`|<span data-ttu-id="d1536-117">Označuje, že první adresa je v části a druhá adresa je posun.</span><span class="sxs-lookup"><span data-stu-id="d1536-117">Indicates that the first address is the section and the second address is an offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d1536-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d1536-118">Requirements</span></span>  
 <span data-ttu-id="d1536-119">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d1536-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1536-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1536-120">See Also</span></span>  
 [<span data-ttu-id="d1536-121">Výčty úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="d1536-121">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
