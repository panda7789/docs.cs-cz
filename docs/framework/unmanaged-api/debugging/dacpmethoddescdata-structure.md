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
ms.openlocfilehash: 97079b824dbd0e056374af4173e49304babd6c32
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739129"
---
# <a name="dacpmethoddescdata-structure"></a><span data-ttu-id="70192-102">DacpMethodDescData – struktura</span><span class="sxs-lookup"><span data-stu-id="70192-102">DacpMethodDescData Structure</span></span>

<span data-ttu-id="70192-103">Definuje přenos vyrovnávací paměť pro informace o modulu runtime metody.</span><span class="sxs-lookup"><span data-stu-id="70192-103">Defines a transport buffer for a method's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="70192-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70192-104">Syntax</span></span>

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

## <a name="members"></a><span data-ttu-id="70192-105">Členové</span><span class="sxs-lookup"><span data-stu-id="70192-105">Members</span></span>

| <span data-ttu-id="70192-106">Člen</span><span class="sxs-lookup"><span data-stu-id="70192-106">Member</span></span>                       | <span data-ttu-id="70192-107">Popis</span><span class="sxs-lookup"><span data-stu-id="70192-107">Description</span></span>                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | <span data-ttu-id="70192-108">Uvádí, zda modul runtime má nativní kód je k dispozici pro danou instanci metody.</span><span class="sxs-lookup"><span data-stu-id="70192-108">Indicates if the runtime has native code available for the given instantiation of the method.</span></span> |
| `bIsDynamic`                 | <span data-ttu-id="70192-109">Označuje, pokud je metoda dynamicky generované prostřednictvím generování lehký kód.</span><span class="sxs-lookup"><span data-stu-id="70192-109">Indicates if the method is generated dynamically through lightweight code generation.</span></span>           |
| `wSlotNumber`                | <span data-ttu-id="70192-110">Číslo pozice metody v tabulce – metoda</span><span class="sxs-lookup"><span data-stu-id="70192-110">The method's slot number in the method table.</span></span>                                                   |
| `NativeCodeAddr`             | <span data-ttu-id="70192-111">Počáteční adresa nativní metody.</span><span class="sxs-lookup"><span data-stu-id="70192-111">The method's initial native address.</span></span>                                                            |
| `data`                       | <span data-ttu-id="70192-112">Ukazatel do vyrovnávací paměti interně modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="70192-112">Pointer to a buffer used internally by the runtime.</span></span>                                             |
| `MethodDescPtr`              | <span data-ttu-id="70192-113">Ukazatel `MethodDesc` v modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="70192-113">Pointer to the `MethodDesc` in the runtime.</span></span>                                                     |
| `nativeCodeInfo`             | <span data-ttu-id="70192-114">Ukazatel do vyrovnávací paměti modulem runtime interně používá ke sledování metody.</span><span class="sxs-lookup"><span data-stu-id="70192-114">Pointer to a buffer used internally by the runtime to track methods.</span></span>                            |
| `moduleInfo`                 | <span data-ttu-id="70192-115">Ukazatel do vyrovnávací paměti interně modulem runtime pro informace o modulu.</span><span class="sxs-lookup"><span data-stu-id="70192-115">Pointer to a buffer used internally by the runtime for module information.</span></span>                      |
| `MDToken`                    | <span data-ttu-id="70192-116">Token přidružený k dané metody.</span><span class="sxs-lookup"><span data-stu-id="70192-116">Token associated with the given method.</span></span>                                                         |
| `payloadGC`                  | <span data-ttu-id="70192-117">Ukazatel do vyrovnávací paměti, uvolňování paměti kolekce interně modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="70192-117">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `payloadGC2`                 | <span data-ttu-id="70192-118">Ukazatel do vyrovnávací paměti, uvolňování paměti kolekce interně modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="70192-118">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `managedDynamicMethodObject` | <span data-ttu-id="70192-119">Pokud je dynamická metoda, modul runtime této vyrovnávací paměti interně používá pro informace o sledování.</span><span class="sxs-lookup"><span data-stu-id="70192-119">If the method is dynamic, the runtime uses this buffer internally for information tracking.</span></span>     |
| `requestedIP`                | <span data-ttu-id="70192-120">Použít k naplnění struktura každý požadavek při adresu nativní kód.</span><span class="sxs-lookup"><span data-stu-id="70192-120">Used to populate the structure per request when given a native code address.</span></span>                    |
| `rejitDataCurrent`           | <span data-ttu-id="70192-121">Informace o instrumentovanou verzí metody.</span><span class="sxs-lookup"><span data-stu-id="70192-121">Information about the latest instrumented version of the method.</span></span>                                   |
| `rejitDataRequested`         | <span data-ttu-id="70192-122">Informace o Rejit pro požadovanou nativní adresu.</span><span class="sxs-lookup"><span data-stu-id="70192-122">Rejit information for the requested native address.</span></span>                                             |
| `cJittedRejitVersions`       | <span data-ttu-id="70192-123">Počet pokusů, které metoda byla rejitted prostřednictvím instrumentace.</span><span class="sxs-lookup"><span data-stu-id="70192-123">Number of times the method has been rejitted through instrumentation.</span></span>                           |

## <a name="remarks"></a><span data-ttu-id="70192-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70192-124">Remarks</span></span>

<span data-ttu-id="70192-125">Tato struktura se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven.</span><span class="sxs-lookup"><span data-stu-id="70192-125">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="70192-126">Pro použití je třeba definujte strukturu jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="70192-126">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="70192-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70192-127">Requirements</span></span>
<span data-ttu-id="70192-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70192-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="70192-129">**Záhlaví:** Žádný</span><span class="sxs-lookup"><span data-stu-id="70192-129">**Header:** None</span></span>  
<span data-ttu-id="70192-130">**Knihovna:** Žádné</span><span class="sxs-lookup"><span data-stu-id="70192-130">**Library:** None</span></span>  
<span data-ttu-id="70192-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="70192-131">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="70192-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70192-132">See also</span></span>

- [<span data-ttu-id="70192-133">Ladění</span><span class="sxs-lookup"><span data-stu-id="70192-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="70192-134">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="70192-134">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="70192-135">Běžné typy dat</span><span class="sxs-lookup"><span data-stu-id="70192-135">Common Data Types</span></span>](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)
