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
ms.openlocfilehash: d623fe862eaf5902fd89d0e512dd07f73a03246f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860814"
---
# <a name="dacpmethoddescdata-structure"></a><span data-ttu-id="4f490-102">DacpMethodDescData – struktura</span><span class="sxs-lookup"><span data-stu-id="4f490-102">DacpMethodDescData Structure</span></span>

<span data-ttu-id="4f490-103">Definuje přenosovou vyrovnávací paměť pro běhové informace metody.</span><span class="sxs-lookup"><span data-stu-id="4f490-103">Defines a transport buffer for a method's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="4f490-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f490-104">Syntax</span></span>

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

## <a name="members"></a><span data-ttu-id="4f490-105">Členové</span><span class="sxs-lookup"><span data-stu-id="4f490-105">Members</span></span>

| <span data-ttu-id="4f490-106">Člen</span><span class="sxs-lookup"><span data-stu-id="4f490-106">Member</span></span>                       | <span data-ttu-id="4f490-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4f490-107">Description</span></span>                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | <span data-ttu-id="4f490-108">Určuje, zda má modul runtime pro danou instanci metody k dispozici nativní kód.</span><span class="sxs-lookup"><span data-stu-id="4f490-108">Indicates if the runtime has native code available for the given instantiation of the method.</span></span> |
| `bIsDynamic`                 | <span data-ttu-id="4f490-109">Určuje, zda je metoda generována dynamicky prostřednictvím zjednodušeného generování kódu.</span><span class="sxs-lookup"><span data-stu-id="4f490-109">Indicates if the method is generated dynamically through lightweight code generation.</span></span>           |
| `wSlotNumber`                | <span data-ttu-id="4f490-110">Číslo pozice metody v tabulce metod.</span><span class="sxs-lookup"><span data-stu-id="4f490-110">The method's slot number in the method table.</span></span>                                                   |
| `NativeCodeAddr`             | <span data-ttu-id="4f490-111">Počáteční nativní adresa metody</span><span class="sxs-lookup"><span data-stu-id="4f490-111">The method's initial native address.</span></span>                                                            |
| `data`                       | <span data-ttu-id="4f490-112">Ukazatel na vyrovnávací paměť použitou interně modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="4f490-112">Pointer to a buffer used internally by the runtime.</span></span>                                             |
| `MethodDescPtr`              | <span data-ttu-id="4f490-113">Ukazatel na modul `MethodDesc` v modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="4f490-113">Pointer to the `MethodDesc` in the runtime.</span></span>                                                     |
| `nativeCodeInfo`             | <span data-ttu-id="4f490-114">Ukazatel na vyrovnávací paměť použitou interně modulem runtime ke sledování metod.</span><span class="sxs-lookup"><span data-stu-id="4f490-114">Pointer to a buffer used internally by the runtime to track methods.</span></span>                            |
| `moduleInfo`                 | <span data-ttu-id="4f490-115">Ukazatel na vyrovnávací paměť použitou interně modulem runtime pro informace o modulu.</span><span class="sxs-lookup"><span data-stu-id="4f490-115">Pointer to a buffer used internally by the runtime for module information.</span></span>                      |
| `MDToken`                    | <span data-ttu-id="4f490-116">Token přidružený k dané metodě</span><span class="sxs-lookup"><span data-stu-id="4f490-116">Token associated with the given method.</span></span>                                                         |
| `payloadGC`                  | <span data-ttu-id="4f490-117">Ukazatel na vyrovnávací paměť pro uvolňování paměti, která se používá interně modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="4f490-117">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `payloadGC2`                 | <span data-ttu-id="4f490-118">Ukazatel na vyrovnávací paměť pro uvolňování paměti, která se používá interně modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="4f490-118">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `managedDynamicMethodObject` | <span data-ttu-id="4f490-119">Pokud je metoda dynamická, modul runtime tuto vyrovnávací paměť interně používá ke sledování informací.</span><span class="sxs-lookup"><span data-stu-id="4f490-119">If the method is dynamic, the runtime uses this buffer internally for information tracking.</span></span>     |
| `requestedIP`                | <span data-ttu-id="4f490-120">Používá se k naplnění struktury na požadavek v případě, že se předává adresa nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="4f490-120">Used to populate the structure per request when given a native code address.</span></span>                    |
| `rejitDataCurrent`           | <span data-ttu-id="4f490-121">Informace o nejnovější instrumentované verzi metody.</span><span class="sxs-lookup"><span data-stu-id="4f490-121">Information about the latest instrumented version of the method.</span></span>                                   |
| `rejitDataRequested`         | <span data-ttu-id="4f490-122">ReJIT informace o požadované nativní adrese.</span><span class="sxs-lookup"><span data-stu-id="4f490-122">Rejit information for the requested native address.</span></span>                                             |
| `cJittedRejitVersions`       | <span data-ttu-id="4f490-123">Počet pokusů, kolikrát se metoda rejitted prostřednictvím instrumentace.</span><span class="sxs-lookup"><span data-stu-id="4f490-123">Number of times the method has been rejitted through instrumentation.</span></span>                           |

## <a name="remarks"></a><span data-ttu-id="4f490-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4f490-124">Remarks</span></span>

<span data-ttu-id="4f490-125">Tato struktura žije v modulu runtime a není vystavena prostřednictvím žádné hlavičky nebo souborů knihoven.</span><span class="sxs-lookup"><span data-stu-id="4f490-125">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="4f490-126">Pokud ho chcete použít, definujte strukturu, jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="4f490-126">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="4f490-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4f490-127">Requirements</span></span>
<span data-ttu-id="4f490-128">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f490-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="4f490-129">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="4f490-129">**Header:** None</span></span>  
<span data-ttu-id="4f490-130">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="4f490-130">**Library:** None</span></span>  
<span data-ttu-id="4f490-131">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4f490-131">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="4f490-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="4f490-132">See also</span></span>

- [<span data-ttu-id="4f490-133">Ladění</span><span class="sxs-lookup"><span data-stu-id="4f490-133">Debugging</span></span>](index.md)
- [<span data-ttu-id="4f490-134">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="4f490-134">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="4f490-135">Běžné typy dat</span><span class="sxs-lookup"><span data-stu-id="4f490-135">Common Data Types</span></span>](../common-data-types-unmanaged-api-reference.md)
