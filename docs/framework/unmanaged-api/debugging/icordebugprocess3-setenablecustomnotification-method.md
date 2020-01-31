---
title: ICorDebugProcess3::SetEnableCustomNotification – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3.SetEnableCustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type:
- apiref
ms.openlocfilehash: f2f365f3fe1568f2dd3bad677dd77a13946002e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792470"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a><span data-ttu-id="d7d43-102">ICorDebugProcess3::SetEnableCustomNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="d7d43-102">ICorDebugProcess3::SetEnableCustomNotification Method</span></span>
<span data-ttu-id="d7d43-103">Povolí nebo zakáže oznámení vlastního ladicího programu určeného typu.</span><span class="sxs-lookup"><span data-stu-id="d7d43-103">Enables and disables custom debugger notifications of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7d43-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7d43-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7d43-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7d43-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="d7d43-106">pro Typ, který určuje vlastní oznámení ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="d7d43-106">[in] The type that specifies custom debugger notifications.</span></span>  
  
 `fEnable`  
 <span data-ttu-id="d7d43-107">[in] `true` povolit oznámení vlastního ladicího programu; `false` zakázat oznámení.</span><span class="sxs-lookup"><span data-stu-id="d7d43-107">[in] `true` to enable custom debugger notifications; `false` to disable notifications.</span></span> <span data-ttu-id="d7d43-108">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="d7d43-108">The default value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7d43-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d7d43-109">Remarks</span></span>  
 <span data-ttu-id="d7d43-110">Pokud je `fEnable` nastaveno na `true`, volání metody <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> spustí zpětné volání [ICorDebugManagedCallback3 –:: CustomNotification –](icordebugmanagedcallback3-customnotification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d7d43-110">When `fEnable` is set to `true`, calls to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method trigger an [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) callback.</span></span> <span data-ttu-id="d7d43-111">Ve výchozím nastavení jsou oznámení zakázána. Proto musí ladicí program určit jakékoli typy oznámení, o kterých ví a který chce zpracovat.</span><span class="sxs-lookup"><span data-stu-id="d7d43-111">Notifications are disabled by default; therefore, the debugger must specify any notification types it knows about and wants to handle.</span></span> <span data-ttu-id="d7d43-112">Vzhledem k tomu, že třída [ICorDebugClass](icordebug-interface.md) je vymezena doménou aplikace, ladicí program musí volat `SetEnableCustomNotification` pro každou doménu aplikace v procesu, pokud chce obdržet oznámení v celém procesu.</span><span class="sxs-lookup"><span data-stu-id="d7d43-112">Because the [ICorDebugClass](icordebug-interface.md) class is scoped by application domain, the debugger must call `SetEnableCustomNotification` for every application domain in the process if it wants to receive the notification across the entire process.</span></span>  
  
 <span data-ttu-id="d7d43-113">Od .NET Framework 4 je jediným podporovaným oznámením oznámení o závislostech mezi vlákny.</span><span class="sxs-lookup"><span data-stu-id="d7d43-113">Starting with the .NET Framework 4, the only supported notification is a cross-thread dependency notification.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7d43-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7d43-114">Requirements</span></span>  
 <span data-ttu-id="d7d43-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7d43-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7d43-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d7d43-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7d43-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d7d43-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7d43-118">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7d43-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7d43-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7d43-119">See also</span></span>

- [<span data-ttu-id="d7d43-120">ICorDebugProcess3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7d43-120">ICorDebugProcess3 Interface</span></span>](icordebugprocess3-interface.md)
- [<span data-ttu-id="d7d43-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d7d43-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d7d43-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="d7d43-122">Debugging</span></span>](index.md)
