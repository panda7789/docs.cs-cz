---
title: ICorDebugManagedCallback::UpdateModuleSymbols – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UpdateModuleSymbols
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UpdateModuleSymbols
helpviewer_keywords:
- UpdateModuleSymbols method [.NET Framework debugging]
- ICorDebugManagedCallback::UpdateModuleSymbols method [.NET Framework debugging]
ms.assetid: 0863f644-58e8-45a0-b0c3-a28e99b20938
topic_type:
- apiref
ms.openlocfilehash: 1f5b413ffbbc8fccbea38f23d8c87d40e010dd37
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130619"
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a><span data-ttu-id="d8d2f-102">ICorDebugManagedCallback::UpdateModuleSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="d8d2f-102">ICorDebugManagedCallback::UpdateModuleSymbols Method</span></span>
<span data-ttu-id="d8d2f-103">Oznamuje ladicímu programu, že se změnily symboly pro modul CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="d8d2f-103">Notifies the debugger that the symbols for a common language runtime module have changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8d2f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8d2f-104">Syntax</span></span>  
  
```cpp  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8d2f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8d2f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d8d2f-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující modul, ve kterém byly symboly změněny.</span><span class="sxs-lookup"><span data-stu-id="d8d2f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the module in which the symbols have changed.</span></span>  
  
 `pModule`  
 <span data-ttu-id="d8d2f-107">pro Ukazatel na objekt ICorDebugModule, který představuje modul, ve kterém byly symboly změněny.</span><span class="sxs-lookup"><span data-stu-id="d8d2f-107">[in] A pointer to an ICorDebugModule object that represents the module in which the symbols have changed.</span></span>  
  
 `pSymbolStream`  
 <span data-ttu-id="d8d2f-108">pro Ukazatel na objekt Win32 COM `IStream`, který obsahuje upravené symboly.</span><span class="sxs-lookup"><span data-stu-id="d8d2f-108">[in] A pointer to a Win32 COM `IStream` object that contains the modified symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8d2f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8d2f-109">Remarks</span></span>  
 <span data-ttu-id="d8d2f-110">Tato metoda poskytuje možnost aktualizovat zobrazení symbolů modulu v ladicím programu voláním [ISymUnmanagedReader:: UpdateSymbolStore –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) nebo [ISymUnmanagedReader:: ReplaceSymbolStore –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span><span class="sxs-lookup"><span data-stu-id="d8d2f-110">This method provides an opportunity to update the debugger's view of a module's symbols by calling [ISymUnmanagedReader::UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) or [ISymUnmanagedReader::ReplaceSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span></span>  
  
 <span data-ttu-id="d8d2f-111">Toto zpětné volání může být pro stejný modul provedeno několikrát.</span><span class="sxs-lookup"><span data-stu-id="d8d2f-111">This callback can occur multiple times for the same module.</span></span>  
  
 <span data-ttu-id="d8d2f-112">Ladicí program by se měl pokoušet svázat zarážky na úrovni nevázaného zdroje.</span><span class="sxs-lookup"><span data-stu-id="d8d2f-112">A debugger should try to bind unbound source-level breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8d2f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8d2f-113">Requirements</span></span>  
 <span data-ttu-id="d8d2f-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8d2f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8d2f-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d8d2f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8d2f-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d8d2f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8d2f-117">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8d2f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8d2f-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8d2f-118">See also</span></span>

- [<span data-ttu-id="d8d2f-119">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d8d2f-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
