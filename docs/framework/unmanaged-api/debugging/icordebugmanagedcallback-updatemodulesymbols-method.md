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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0a506f05aac3b8335a0863c3152567fe05463a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415877"
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a><span data-ttu-id="88265-102">ICorDebugManagedCallback::UpdateModuleSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="88265-102">ICorDebugManagedCallback::UpdateModuleSymbols Method</span></span>
<span data-ttu-id="88265-103">Upozorní ladicí program, že došlo ke změně symboly pro běžné modul runtime jazyka.</span><span class="sxs-lookup"><span data-stu-id="88265-103">Notifies the debugger that the symbols for a common language runtime module have changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88265-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88265-104">Syntax</span></span>  
  
```  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="88265-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="88265-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="88265-106">[v] Ukazatel na ICorDebugAppDomain objekt, který reprezentuje obsahující modul, ve kterém symboly změnili domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="88265-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the module in which the symbols have changed.</span></span>  
  
 `pModule`  
 <span data-ttu-id="88265-107">[v] Ukazatel na ICorDebugModule objekt, který představuje modul, ve kterém symboly změnily.</span><span class="sxs-lookup"><span data-stu-id="88265-107">[in] A pointer to an ICorDebugModule object that represents the module in which the symbols have changed.</span></span>  
  
 `pSymbolStream`  
 <span data-ttu-id="88265-108">[v] Ukazatel na Win32 COM `IStream` objekt, který obsahuje upravené symboly.</span><span class="sxs-lookup"><span data-stu-id="88265-108">[in] A pointer to a Win32 COM `IStream` object that contains the modified symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88265-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="88265-109">Remarks</span></span>  
 <span data-ttu-id="88265-110">Tato metoda vám dává příležitost k aktualizaci zobrazení ladicího programu modul symbolů voláním [isymunmanagedreader::updatesymbolstore –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) nebo [isymunmanagedreader::replacesymbolstore –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span><span class="sxs-lookup"><span data-stu-id="88265-110">This method provides an opportunity to update the debugger's view of a module's symbols by calling [ISymUnmanagedReader::UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) or [ISymUnmanagedReader::ReplaceSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span></span>  
  
 <span data-ttu-id="88265-111">Tato zpětného volání může mít více než jednou. stejný modul.</span><span class="sxs-lookup"><span data-stu-id="88265-111">This callback can occur multiple times for the same module.</span></span>  
  
 <span data-ttu-id="88265-112">Ladicí program se pokuste vytvořit vazbu nevázaný zarážky úrovně zdroje.</span><span class="sxs-lookup"><span data-stu-id="88265-112">A debugger should try to bind unbound source-level breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88265-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="88265-113">Requirements</span></span>  
 <span data-ttu-id="88265-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88265-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88265-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88265-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88265-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88265-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88265-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88265-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88265-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="88265-118">See Also</span></span>  
 [<span data-ttu-id="88265-119">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="88265-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
