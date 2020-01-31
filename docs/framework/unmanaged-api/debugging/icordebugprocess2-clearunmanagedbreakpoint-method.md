---
title: ICorDebugProcess2::ClearUnmanagedBreakpoint – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type:
- apiref
ms.openlocfilehash: e2aaf902afd71a4a81f7d64ef3fec046aacc91fc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792534"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="77978-102">ICorDebugProcess2::ClearUnmanagedBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="77978-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="77978-103">Odebere dříve nastavenou zarážku na dané adrese.</span><span class="sxs-lookup"><span data-stu-id="77978-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77978-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77978-104">Syntax</span></span>  
  
```cpp  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77978-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="77978-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="77978-106">pro Hodnota `CORDB_ADDRESS` určující adresu, na které byla zarážka nastavena.</span><span class="sxs-lookup"><span data-stu-id="77978-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77978-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="77978-107">Remarks</span></span>  
 <span data-ttu-id="77978-108">Zadaná zarážka by byla dříve nastavena starším voláním metody [ICorDebugProcess2:: SetUnmanagedBreakpoint –](icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="77978-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="77978-109">Metodu `ClearUnmanagedBreakpoint` lze volat, pokud je spuštěn proces ladění.</span><span class="sxs-lookup"><span data-stu-id="77978-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="77978-110">Metoda `ClearUnmanagedBreakpoint` vrátí kód chyby, pokud je ladicí program připojen v režimu pouze spravovaném, nebo pokud na zadané adrese neexistuje žádná zarážka.</span><span class="sxs-lookup"><span data-stu-id="77978-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77978-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="77978-111">Requirements</span></span>  
 <span data-ttu-id="77978-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77978-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77978-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="77978-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77978-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="77978-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77978-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77978-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
