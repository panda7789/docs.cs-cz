---
title: ICorDebugDataTarget::GetPlatform – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetPlatform Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type:
- apiref
ms.openlocfilehash: 3df35d52a4e5209b282ccef653b065bdcf1f8fe4
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976535"
---
# <a name="icordebugdatatargetgetplatform-method"></a><span data-ttu-id="48c82-102">ICorDebugDataTarget::GetPlatform – metoda</span><span class="sxs-lookup"><span data-stu-id="48c82-102">ICorDebugDataTarget::GetPlatform Method</span></span>
<span data-ttu-id="48c82-103">Obsahuje informace o platformě, včetně architektury procesoru a operačního systému, na kterých je spuštěn cílový proces.</span><span class="sxs-lookup"><span data-stu-id="48c82-103">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48c82-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48c82-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48c82-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="48c82-105">Parameters</span></span>  
 `pTargetPlatform`  
 <span data-ttu-id="48c82-106">mimo Ukazatel na výčet [CorDebugPlatformEnum –](cordebugplatform-enumeration.md) , který popisuje cílovou platformu.</span><span class="sxs-lookup"><span data-stu-id="48c82-106">[out] A pointer to a [CorDebugPlatformEnum](cordebugplatform-enumeration.md) enumeration that describes the target platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48c82-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="48c82-107">Remarks</span></span>  
 <span data-ttu-id="48c82-108">Návratová hodnota `CorDebugPlatformEnum` výčtu je používána rozhraním [ICorDebug](icordebug-interface.md) k určení podrobností o cílovém procesu, jako je jeho velikost ukazatele, rozložení adresního prostoru, sada registrů, formát instrukcí, rozložení kontextu a konvence volání.</span><span class="sxs-lookup"><span data-stu-id="48c82-108">The `CorDebugPlatformEnum` enumeration return value is used by the [ICorDebug](icordebug-interface.md) interface to determine details of the target process such as its pointer size, address space layout, register set, instruction format, context layout, and calling conventions.</span></span>  
  
 <span data-ttu-id="48c82-109">`pTargetPlatform` Hodnota se může vztahovat na platformu, která je emulovaná pro cíl, a ne zadání samotného používaného hardwaru.</span><span class="sxs-lookup"><span data-stu-id="48c82-109">The `pTargetPlatform` value may refer to a platform that is being emulated for the target instead of specifying the actual hardware in use.</span></span> <span data-ttu-id="48c82-110">Například proces, který je spuštěný v prostředí Windows on Windows (WOW) na 64 edici operačního systému Windows, by měl používat `CORDB_PLATFORM_WINDOWS_X86` hodnotu výčtu [CorDebugPlatformEnum –](cordebugplatform-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="48c82-110">For example, a process that is running in the Windows on Windows (WOW) environment on a 64-bit edition of the Windows operating system should use the `CORDB_PLATFORM_WINDOWS_X86` value of the [CorDebugPlatformEnum](cordebugplatform-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="48c82-111">Tato metoda musí být úspěšná.</span><span class="sxs-lookup"><span data-stu-id="48c82-111">This method must succeed.</span></span> <span data-ttu-id="48c82-112">Pokud dojde k chybě, cílová platforma nebude použitelná.</span><span class="sxs-lookup"><span data-stu-id="48c82-112">If it fails, the target platform is unusable.</span></span> <span data-ttu-id="48c82-113">Tato metoda může selhat z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="48c82-113">The method may fail for the following reasons:</span></span>  
  
- <span data-ttu-id="48c82-114">Platforma, která je emulovana pro cíl, je nepoužitelná.</span><span class="sxs-lookup"><span data-stu-id="48c82-114">The platform that is being emulated for the target is unusable.</span></span>  
  
- <span data-ttu-id="48c82-115">Skutečný hardware na cílové platformě je nepoužitelný.</span><span class="sxs-lookup"><span data-stu-id="48c82-115">The actual hardware on the target platform is unusable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48c82-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="48c82-116">Requirements</span></span>  
 <span data-ttu-id="48c82-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48c82-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48c82-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="48c82-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48c82-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="48c82-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48c82-120">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48c82-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48c82-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="48c82-121">See also</span></span>

- [<span data-ttu-id="48c82-122">ICorDebugDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="48c82-122">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="48c82-123">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="48c82-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="48c82-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="48c82-124">Debugging</span></span>](index.md)
