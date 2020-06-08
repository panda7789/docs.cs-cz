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
ms.openlocfilehash: c0381cf924e44e581c8b275c9750cacba045cf1b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501778"
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a><span data-ttu-id="5f3dd-102">ICorDebugManagedCallback::UpdateModuleSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="5f3dd-102">ICorDebugManagedCallback::UpdateModuleSymbols Method</span></span>
<span data-ttu-id="5f3dd-103">Oznamuje ladicímu programu, že se změnily symboly pro modul CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="5f3dd-103">Notifies the debugger that the symbols for a common language runtime module have changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f3dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f3dd-104">Syntax</span></span>  
  
```cpp  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f3dd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f3dd-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="5f3dd-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující modul, ve kterém byly symboly změněny.</span><span class="sxs-lookup"><span data-stu-id="5f3dd-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the module in which the symbols have changed.</span></span>  
  
 `pModule`  
 <span data-ttu-id="5f3dd-107">pro Ukazatel na objekt ICorDebugModule, který představuje modul, ve kterém byly symboly změněny.</span><span class="sxs-lookup"><span data-stu-id="5f3dd-107">[in] A pointer to an ICorDebugModule object that represents the module in which the symbols have changed.</span></span>  
  
 `pSymbolStream`  
 <span data-ttu-id="5f3dd-108">pro Ukazatel na objekt modelu COM Win32 `IStream` , který obsahuje upravené symboly.</span><span class="sxs-lookup"><span data-stu-id="5f3dd-108">[in] A pointer to a Win32 COM `IStream` object that contains the modified symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f3dd-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5f3dd-109">Remarks</span></span>  
 <span data-ttu-id="5f3dd-110">Tato metoda poskytuje možnost aktualizovat zobrazení symbolů modulu v ladicím programu voláním [ISymUnmanagedReader:: UpdateSymbolStore –](../diagnostics/isymunmanagedreader-updatesymbolstore-method.md) nebo [ISymUnmanagedReader:: ReplaceSymbolStore –](../diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span><span class="sxs-lookup"><span data-stu-id="5f3dd-110">This method provides an opportunity to update the debugger's view of a module's symbols by calling [ISymUnmanagedReader::UpdateSymbolStore](../diagnostics/isymunmanagedreader-updatesymbolstore-method.md) or [ISymUnmanagedReader::ReplaceSymbolStore](../diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span></span>  
  
 <span data-ttu-id="5f3dd-111">Toto zpětné volání může být pro stejný modul provedeno několikrát.</span><span class="sxs-lookup"><span data-stu-id="5f3dd-111">This callback can occur multiple times for the same module.</span></span>  
  
 <span data-ttu-id="5f3dd-112">Ladicí program by se měl pokoušet svázat zarážky na úrovni nevázaného zdroje.</span><span class="sxs-lookup"><span data-stu-id="5f3dd-112">A debugger should try to bind unbound source-level breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f3dd-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5f3dd-113">Requirements</span></span>  
 <span data-ttu-id="5f3dd-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f3dd-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f3dd-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5f3dd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f3dd-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5f3dd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f3dd-117">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f3dd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f3dd-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f3dd-118">See also</span></span>

- [<span data-ttu-id="5f3dd-119">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f3dd-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
