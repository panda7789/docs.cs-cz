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
ms.openlocfilehash: 5991b0abaedabe2337cd754c7bd19f96c5e9b685
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420614"
---
# <a name="corsymaddrkind-enumeration"></a><span data-ttu-id="929be-102">CorSymAddrKind – výčet</span><span class="sxs-lookup"><span data-stu-id="929be-102">CorSymAddrKind Enumeration</span></span>
<span data-ttu-id="929be-103">Určuje typ adresy paměti.</span><span class="sxs-lookup"><span data-stu-id="929be-103">Indicates the type of memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="929be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="929be-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="929be-105">Členové</span><span class="sxs-lookup"><span data-stu-id="929be-105">Members</span></span>  
  
|<span data-ttu-id="929be-106">Člen</span><span class="sxs-lookup"><span data-stu-id="929be-106">Member</span></span>|<span data-ttu-id="929be-107">Popis</span><span class="sxs-lookup"><span data-stu-id="929be-107">Description</span></span>|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|<span data-ttu-id="929be-108">Označuje místní proměnnou nebo index parametru jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="929be-108">Indicates a Microsoft intermediate language (MSIL) local variable or parameter index.</span></span>|  
|`ADDR_NATIVE_RVA`|<span data-ttu-id="929be-109">Označuje relativní virtuální adresu do modulu.</span><span class="sxs-lookup"><span data-stu-id="929be-109">Indicates a relative virtual address into a module.</span></span>|  
|`ADDR_NATIVE_REGISTER`|<span data-ttu-id="929be-110">Označuje registr procesoru.</span><span class="sxs-lookup"><span data-stu-id="929be-110">Indicates a CPU register.</span></span>|  
|`ADDR_NATIVE_REGREL`|<span data-ttu-id="929be-111">Označuje, že první adresa je registr a druhá adresa je posun.</span><span class="sxs-lookup"><span data-stu-id="929be-111">Indicates that the first address is a register and the second address is an offset.</span></span>|  
|`ADDR_NATIVE_OFFSET`|<span data-ttu-id="929be-112">Označuje posun od základní adresy.</span><span class="sxs-lookup"><span data-stu-id="929be-112">Indicates an offset from a base address.</span></span>|  
|`ADDR_NATIVE_REGREG`|<span data-ttu-id="929be-113">Označuje, že první adresa je dolní část registru, a druhá adresa je horní část.</span><span class="sxs-lookup"><span data-stu-id="929be-113">Indicates that the first address is the low portion of a register, and the second address is the high portion.</span></span>|  
|`ADDR_NATIVE_REGSTK`|<span data-ttu-id="929be-114">Označuje, že první adresa je dolní část registru, druhá je horní část a třetí je posun.</span><span class="sxs-lookup"><span data-stu-id="929be-114">Indicates that the first address is the low portion of a register, the second is the high portion, and the third is an offset.</span></span>|  
|`ADDR_NATIVE_STKREG`|<span data-ttu-id="929be-115">Označuje, že první adresa je registr, druhým je posun a třetí je vysoká část registru.</span><span class="sxs-lookup"><span data-stu-id="929be-115">Indicates that the first address is a register, the second is an offset, and the third is the high portion of the register.</span></span>|  
|`ADDR_BITFIELD`|<span data-ttu-id="929be-116">Označuje, že první adresa je začátek pole a druhá adresa je délka pole.</span><span class="sxs-lookup"><span data-stu-id="929be-116">Indicates that the first address is the start of a field and the second address is the field length.</span></span>|  
|`ADDR_NATIVE_ISECTOFFSET`|<span data-ttu-id="929be-117">Označuje, že první adresa je oddíl a druhá adresa je posun.</span><span class="sxs-lookup"><span data-stu-id="929be-117">Indicates that the first address is the section and the second address is an offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="929be-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="929be-118">Requirements</span></span>  
 <span data-ttu-id="929be-119">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="929be-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="929be-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="929be-120">See also</span></span>

- [<span data-ttu-id="929be-121">Výčty úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="929be-121">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
