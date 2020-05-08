---
title: ICorDebugDataTarget2::GetSymbolProviderForImage – metoda
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
ms.openlocfilehash: 7800630be0ed9afb321d607046be308088781388
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976444"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="bab19-102">ICorDebugDataTarget2::GetSymbolProviderForImage – metoda</span><span class="sxs-lookup"><span data-stu-id="bab19-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="bab19-103">Vrátí poskytovatele symbolů pro modul ze základní adresy tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="bab19-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bab19-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bab19-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bab19-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bab19-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="bab19-106">pro Hodnota [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) , která představuje základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="bab19-106">[in] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="bab19-107">mimo Ukazatel na adresu [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="bab19-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bab19-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bab19-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bab19-109">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bab19-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bab19-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bab19-110">Requirements</span></span>  
 <span data-ttu-id="bab19-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bab19-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bab19-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bab19-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bab19-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bab19-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bab19-114">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bab19-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bab19-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="bab19-115">See also</span></span>

- [<span data-ttu-id="bab19-116">Rozhraní ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="bab19-116">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="bab19-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bab19-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
