---
title: ICorDebugSymbolProvider2::GetFrameProps Method
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 274da030bbbb7c614709b5150f08f37ddf5aaf5a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771162"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="e65be-102">ICorDebugSymbolProvider2::GetFrameProps Method</span><span class="sxs-lookup"><span data-stu-id="e65be-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="e65be-103">Vrátí metodu počáteční relativní virtuální adresa metodu a daný kód relativní virtuální adresu nadřazeného rámce.</span><span class="sxs-lookup"><span data-stu-id="e65be-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e65be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e65be-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e65be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e65be-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="e65be-106">[in] Kód relativní virtuální adresu.</span><span class="sxs-lookup"><span data-stu-id="e65be-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="e65be-107">[out] Ukazatel způsob spuštění relativní virtuální adresu.</span><span class="sxs-lookup"><span data-stu-id="e65be-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="e65be-108">[out] Ukazatel rámec počáteční relativní virtuální adresa.</span><span class="sxs-lookup"><span data-stu-id="e65be-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e65be-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e65be-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e65be-110">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e65be-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e65be-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e65be-111">Requirements</span></span>  
 <span data-ttu-id="e65be-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e65be-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e65be-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e65be-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e65be-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e65be-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e65be-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e65be-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e65be-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e65be-116">See also</span></span>

- [<span data-ttu-id="e65be-117">ICorDebugSymbolProvider2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e65be-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="e65be-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e65be-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
