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
ms.openlocfilehash: 581ea4f974bfec3961a32cd7c9985a5e45d2bddd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995065"
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a><span data-ttu-id="42219-102">ICorDebugManagedCallback::UpdateModuleSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="42219-102">ICorDebugManagedCallback::UpdateModuleSymbols Method</span></span>
<span data-ttu-id="42219-103">Upozorní ladicího programu, že jste změnili symboly pro společný jazykový modul runtime.</span><span class="sxs-lookup"><span data-stu-id="42219-103">Notifies the debugger that the symbols for a common language runtime module have changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42219-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42219-104">Syntax</span></span>  
  
```  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42219-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42219-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="42219-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující modul, ve kterém jste změnili symboly.</span><span class="sxs-lookup"><span data-stu-id="42219-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the module in which the symbols have changed.</span></span>  
  
 `pModule`  
 <span data-ttu-id="42219-107">[in] Ukazatel na objekt icordebugmodule –, který představuje modul, ve kterém jste změnili symboly.</span><span class="sxs-lookup"><span data-stu-id="42219-107">[in] A pointer to an ICorDebugModule object that represents the module in which the symbols have changed.</span></span>  
  
 `pSymbolStream`  
 <span data-ttu-id="42219-108">[in] Ukazatel na Win32 COM `IStream` objekt, který obsahuje upravený symboly.</span><span class="sxs-lookup"><span data-stu-id="42219-108">[in] A pointer to a Win32 COM `IStream` object that contains the modified symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42219-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42219-109">Remarks</span></span>  
 <span data-ttu-id="42219-110">Tato metoda poskytuje příležitost k aktualizaci zobrazení ladicího programu modulu symbolů voláním [isymunmanagedreader::updatesymbolstore –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) nebo [isymunmanagedreader::replacesymbolstore –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span><span class="sxs-lookup"><span data-stu-id="42219-110">This method provides an opportunity to update the debugger's view of a module's symbols by calling [ISymUnmanagedReader::UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) or [ISymUnmanagedReader::ReplaceSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span></span>  
  
 <span data-ttu-id="42219-111">Toto zpětné volání může mít více než jednou stejného modulu.</span><span class="sxs-lookup"><span data-stu-id="42219-111">This callback can occur multiple times for the same module.</span></span>  
  
 <span data-ttu-id="42219-112">Ladicí program se pokuste vytvořit vazbu nevázaného zarážky úroveň zdroje.</span><span class="sxs-lookup"><span data-stu-id="42219-112">A debugger should try to bind unbound source-level breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42219-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42219-113">Requirements</span></span>  
 <span data-ttu-id="42219-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42219-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42219-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42219-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42219-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42219-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42219-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42219-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42219-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42219-118">See also</span></span>

- [<span data-ttu-id="42219-119">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42219-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
