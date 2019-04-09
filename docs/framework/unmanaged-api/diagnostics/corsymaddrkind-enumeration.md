---
title: CorSymAddrKind – výčet
ms.date: 03/30/2017
api_name:
- CorSymAddrKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymAddrKind
helpviewer_keywords:
- CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: adef1010d08561c0a0fe38480fe0d2f519a80b49
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133520"
---
# <a name="corsymaddrkind-enumeration"></a><span data-ttu-id="9f30c-102">CorSymAddrKind – výčet</span><span class="sxs-lookup"><span data-stu-id="9f30c-102">CorSymAddrKind Enumeration</span></span>
<span data-ttu-id="9f30c-103">Určuje typ přidávané adresy paměti.</span><span class="sxs-lookup"><span data-stu-id="9f30c-103">Indicates the type of memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f30c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f30c-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="9f30c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="9f30c-105">Members</span></span>  
  
|<span data-ttu-id="9f30c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="9f30c-106">Member</span></span>|<span data-ttu-id="9f30c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9f30c-107">Description</span></span>|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|<span data-ttu-id="9f30c-108">Označuje, Microsoft intermediate language (MSIL) místní proměnná nebo parametr indexu.</span><span class="sxs-lookup"><span data-stu-id="9f30c-108">Indicates a Microsoft intermediate language (MSIL) local variable or parameter index.</span></span>|  
|`ADDR_NATIVE_RVA`|<span data-ttu-id="9f30c-109">Určuje relativní virtuální adresu do modulu.</span><span class="sxs-lookup"><span data-stu-id="9f30c-109">Indicates a relative virtual address into a module.</span></span>|  
|`ADDR_NATIVE_REGISTER`|<span data-ttu-id="9f30c-110">Označuje registru procesoru.</span><span class="sxs-lookup"><span data-stu-id="9f30c-110">Indicates a CPU register.</span></span>|  
|`ADDR_NATIVE_REGREL`|<span data-ttu-id="9f30c-111">Označuje, že první adresa registru a druhá adresa je posun.</span><span class="sxs-lookup"><span data-stu-id="9f30c-111">Indicates that the first address is a register and the second address is an offset.</span></span>|  
|`ADDR_NATIVE_OFFSET`|<span data-ttu-id="9f30c-112">Určuje posun od základní adresa.</span><span class="sxs-lookup"><span data-stu-id="9f30c-112">Indicates an offset from a base address.</span></span>|  
|`ADDR_NATIVE_REGREG`|<span data-ttu-id="9f30c-113">Označuje, že první adresa je nízká část registru a druhá adresa je vysoké.</span><span class="sxs-lookup"><span data-stu-id="9f30c-113">Indicates that the first address is the low portion of a register, and the second address is the high portion.</span></span>|  
|`ADDR_NATIVE_REGSTK`|<span data-ttu-id="9f30c-114">Označuje, že první adresa je nízká část registru, druhá je vysoká část a třetí je posun.</span><span class="sxs-lookup"><span data-stu-id="9f30c-114">Indicates that the first address is the low portion of a register, the second is the high portion, and the third is an offset.</span></span>|  
|`ADDR_NATIVE_STKREG`|<span data-ttu-id="9f30c-115">Označuje, že první adresa je registr, posun je druhý a třetí je vysoká část do registru.</span><span class="sxs-lookup"><span data-stu-id="9f30c-115">Indicates that the first address is a register, the second is an offset, and the third is the high portion of the register.</span></span>|  
|`ADDR_BITFIELD`|<span data-ttu-id="9f30c-116">Označuje, že první adresa je začátek pole a druhý adresa je délka pole.</span><span class="sxs-lookup"><span data-stu-id="9f30c-116">Indicates that the first address is the start of a field and the second address is the field length.</span></span>|  
|`ADDR_NATIVE_ISECTOFFSET`|<span data-ttu-id="9f30c-117">Označuje, že první adresa je oddíl a druhá adresa je posun.</span><span class="sxs-lookup"><span data-stu-id="9f30c-117">Indicates that the first address is the section and the second address is an offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9f30c-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f30c-118">Requirements</span></span>  
 <span data-ttu-id="9f30c-119">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9f30c-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f30c-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f30c-120">See also</span></span>

- [<span data-ttu-id="9f30c-121">Výčty úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="9f30c-121">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
