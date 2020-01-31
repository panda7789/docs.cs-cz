---
title: DacpMethodDescData – struktura
ms.date: 02/01/2019
api.name:
- DacpMethodDescData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpMethodDescData Structure
helpviewer.keywords:
- DacpMethodDescData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: cc54664ea8ad61005de3f3fae7407946d1c861b2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793848"
---
# <a name="dacpmethoddescdata-structure"></a><span data-ttu-id="dcf31-102">DacpMethodDescData – struktura</span><span class="sxs-lookup"><span data-stu-id="dcf31-102">DacpMethodDescData Structure</span></span>

<span data-ttu-id="dcf31-103">Definuje přenosovou vyrovnávací paměť pro běhové informace metody.</span><span class="sxs-lookup"><span data-stu-id="dcf31-103">Defines a transport buffer for a method's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="dcf31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcf31-104">Syntax</span></span>

```cpp
struct DacpMethodDescData
{
    int             bHasNativeCode;
    int             bIsDynamic;
    unsigned short  wSlotNumber;
    CLRDATA_ADDRESS NativeCodeAddr;
    CLRDATA_ADDRESS data;
    CLRDATA_ADDRESS MethodDescPtr;
    CLRDATA_ADDRESS nativeCodeInfo;
    CLRDATA_ADDRESS moduleInfo;
    mdToken         MDToken;
    CLRDATA_ADDRESS payloadGC;
    CLRDATA_ADDRESS payloadGC2;
    CLRDATA_ADDRESS managedDynamicMethodObject;
    CLRDATA_ADDRESS requestedIP;
    DacpReJitData   rejitDataCurrent;
    DacpReJitData   rejitDataRequested;
    unsigned long   cJittedRejitVersions;
};
```

## <a name="members"></a><span data-ttu-id="dcf31-105">Členové</span><span class="sxs-lookup"><span data-stu-id="dcf31-105">Members</span></span>

| <span data-ttu-id="dcf31-106">Člen</span><span class="sxs-lookup"><span data-stu-id="dcf31-106">Member</span></span>                       | <span data-ttu-id="dcf31-107">Popis</span><span class="sxs-lookup"><span data-stu-id="dcf31-107">Description</span></span>                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | <span data-ttu-id="dcf31-108">Určuje, zda má modul runtime pro danou instanci metody k dispozici nativní kód.</span><span class="sxs-lookup"><span data-stu-id="dcf31-108">Indicates if the runtime has native code available for the given instantiation of the method.</span></span> |
| `bIsDynamic`                 | <span data-ttu-id="dcf31-109">Určuje, zda je metoda generována dynamicky prostřednictvím zjednodušeného generování kódu.</span><span class="sxs-lookup"><span data-stu-id="dcf31-109">Indicates if the method is generated dynamically through lightweight code generation.</span></span>           |
| `wSlotNumber`                | <span data-ttu-id="dcf31-110">Číslo pozice metody v tabulce metod.</span><span class="sxs-lookup"><span data-stu-id="dcf31-110">The method's slot number in the method table.</span></span>                                                   |
| `NativeCodeAddr`             | <span data-ttu-id="dcf31-111">Počáteční nativní adresa metody</span><span class="sxs-lookup"><span data-stu-id="dcf31-111">The method's initial native address.</span></span>                                                            |
| `data`                       | <span data-ttu-id="dcf31-112">Ukazatel na vyrovnávací paměť použitou interně modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="dcf31-112">Pointer to a buffer used internally by the runtime.</span></span>                                             |
| `MethodDescPtr`              | <span data-ttu-id="dcf31-113">Ukazatel na `MethodDesc` v modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="dcf31-113">Pointer to the `MethodDesc` in the runtime.</span></span>                                                     |
| `nativeCodeInfo`             | <span data-ttu-id="dcf31-114">Ukazatel na vyrovnávací paměť použitou interně modulem runtime ke sledování metod.</span><span class="sxs-lookup"><span data-stu-id="dcf31-114">Pointer to a buffer used internally by the runtime to track methods.</span></span>                            |
| `moduleInfo`                 | <span data-ttu-id="dcf31-115">Ukazatel na vyrovnávací paměť použitou interně modulem runtime pro informace o modulu.</span><span class="sxs-lookup"><span data-stu-id="dcf31-115">Pointer to a buffer used internally by the runtime for module information.</span></span>                      |
| `MDToken`                    | <span data-ttu-id="dcf31-116">Token přidružený k dané metodě</span><span class="sxs-lookup"><span data-stu-id="dcf31-116">Token associated with the given method.</span></span>                                                         |
| `payloadGC`                  | <span data-ttu-id="dcf31-117">Ukazatel na vyrovnávací paměť pro uvolňování paměti, která se používá interně modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="dcf31-117">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `payloadGC2`                 | <span data-ttu-id="dcf31-118">Ukazatel na vyrovnávací paměť pro uvolňování paměti, která se používá interně modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="dcf31-118">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `managedDynamicMethodObject` | <span data-ttu-id="dcf31-119">Pokud je metoda dynamická, modul runtime tuto vyrovnávací paměť interně používá ke sledování informací.</span><span class="sxs-lookup"><span data-stu-id="dcf31-119">If the method is dynamic, the runtime uses this buffer internally for information tracking.</span></span>     |
| `requestedIP`                | <span data-ttu-id="dcf31-120">Používá se k naplnění struktury na požadavek v případě, že se předává adresa nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="dcf31-120">Used to populate the structure per request when given a native code address.</span></span>                    |
| `rejitDataCurrent`           | <span data-ttu-id="dcf31-121">Informace o nejnovější instrumentované verzi metody.</span><span class="sxs-lookup"><span data-stu-id="dcf31-121">Information about the latest instrumented version of the method.</span></span>                                   |
| `rejitDataRequested`         | <span data-ttu-id="dcf31-122">ReJIT informace o požadované nativní adrese.</span><span class="sxs-lookup"><span data-stu-id="dcf31-122">Rejit information for the requested native address.</span></span>                                             |
| `cJittedRejitVersions`       | <span data-ttu-id="dcf31-123">Počet pokusů, kolikrát se metoda rejitted prostřednictvím instrumentace.</span><span class="sxs-lookup"><span data-stu-id="dcf31-123">Number of times the method has been rejitted through instrumentation.</span></span>                           |

## <a name="remarks"></a><span data-ttu-id="dcf31-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dcf31-124">Remarks</span></span>

<span data-ttu-id="dcf31-125">Tato struktura žije v modulu runtime a není vystavena prostřednictvím žádné hlavičky nebo souborů knihoven.</span><span class="sxs-lookup"><span data-stu-id="dcf31-125">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="dcf31-126">Pokud ho chcete použít, definujte strukturu, jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="dcf31-126">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="dcf31-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dcf31-127">Requirements</span></span>
<span data-ttu-id="dcf31-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcf31-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="dcf31-129">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="dcf31-129">**Header:** None</span></span>  
<span data-ttu-id="dcf31-130">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="dcf31-130">**Library:** None</span></span>  
<span data-ttu-id="dcf31-131">**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="dcf31-131">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="dcf31-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dcf31-132">See also</span></span>

- [<span data-ttu-id="dcf31-133">Ladění</span><span class="sxs-lookup"><span data-stu-id="dcf31-133">Debugging</span></span>](index.md)
- [<span data-ttu-id="dcf31-134">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="dcf31-134">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="dcf31-135">Běžné typy dat</span><span class="sxs-lookup"><span data-stu-id="dcf31-135">Common Data Types</span></span>](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)
