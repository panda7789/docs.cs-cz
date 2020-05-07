---
title: ICorDebugAppDomainEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum
helpviewer_keywords:
- ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: e9226e6e-ca2c-428e-bb38-0c099210f507
topic_type:
- apiref
ms.openlocfilehash: 38603fb53b9cd6548595437b05c1e99ef208d940
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895094"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="85638-102">ICorDebugAppDomainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85638-102">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="85638-103">Poskytuje `Next` metodu, která vrací zadaný počet `ICorDebugAppDomainEnum` hodnot od dalšího umístění ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="85638-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="85638-104">Toto rozhraní je podtřídou třídy "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="85638-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="85638-105">Metody</span><span class="sxs-lookup"><span data-stu-id="85638-105">Methods</span></span>  
  
|<span data-ttu-id="85638-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="85638-106">Method</span></span>|<span data-ttu-id="85638-107">Popis</span><span class="sxs-lookup"><span data-stu-id="85638-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85638-108">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="85638-108">Next Method</span></span>](icordebugappdomainenum-next-method.md)|<span data-ttu-id="85638-109">Načte zadaný počet aplikačních domén z kolekce počínaje aktuální pozicí kurzoru.</span><span class="sxs-lookup"><span data-stu-id="85638-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85638-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="85638-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85638-111">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="85638-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85638-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="85638-112">Requirements</span></span>  
 <span data-ttu-id="85638-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85638-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85638-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="85638-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85638-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="85638-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85638-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85638-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85638-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="85638-117">See also</span></span>

- [<span data-ttu-id="85638-118">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85638-118">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="85638-119">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85638-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
