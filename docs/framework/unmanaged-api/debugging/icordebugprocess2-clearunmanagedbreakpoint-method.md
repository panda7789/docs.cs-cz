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
ms.openlocfilehash: 2b228383c3b393fe43f60d39e59cca37af36233f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212487"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="c9dbf-102">ICorDebugProcess2::ClearUnmanagedBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="c9dbf-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="c9dbf-103">Odebere dříve nastavenou zarážku na dané adrese.</span><span class="sxs-lookup"><span data-stu-id="c9dbf-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9dbf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9dbf-104">Syntax</span></span>  
  
```cpp  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9dbf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9dbf-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="c9dbf-106">pro `CORDB_ADDRESS`Hodnota, která určuje adresu, na které byla zarážka nastavena.</span><span class="sxs-lookup"><span data-stu-id="c9dbf-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9dbf-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9dbf-107">Remarks</span></span>  
 <span data-ttu-id="c9dbf-108">Zadaná zarážka by byla dříve nastavena starším voláním metody [ICorDebugProcess2:: SetUnmanagedBreakpoint –](icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="c9dbf-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="c9dbf-109">`ClearUnmanagedBreakpoint`Metodu lze volat, pokud je spuštěn proces ladění.</span><span class="sxs-lookup"><span data-stu-id="c9dbf-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="c9dbf-110">`ClearUnmanagedBreakpoint`Metoda vrátí kód chyby, pokud je ladicí program připojen v režimu pouze spravovaném, nebo pokud na zadané adrese neexistuje žádná zarážka.</span><span class="sxs-lookup"><span data-stu-id="c9dbf-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9dbf-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9dbf-111">Requirements</span></span>  
 <span data-ttu-id="c9dbf-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9dbf-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9dbf-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c9dbf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9dbf-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c9dbf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9dbf-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9dbf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
