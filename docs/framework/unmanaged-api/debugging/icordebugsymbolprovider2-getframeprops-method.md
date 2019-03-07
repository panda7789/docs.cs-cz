---
title: ICorDebugSymbolProvider2::GetFrameProps Method
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c02a2b31ecc588879b43668d56cd9978b62e49a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482480"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="61929-102">ICorDebugSymbolProvider2::GetFrameProps Method</span><span class="sxs-lookup"><span data-stu-id="61929-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="61929-103">Vrátí metodu počáteční relativní virtuální adresa metodu a daný kód relativní virtuální adresu nadřazeného rámce.</span><span class="sxs-lookup"><span data-stu-id="61929-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61929-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61929-104">Syntax</span></span>  
  
```  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61929-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="61929-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="61929-106">[in] Kód relativní virtuální adresu.</span><span class="sxs-lookup"><span data-stu-id="61929-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="61929-107">[out] Ukazatel způsob spuštění relativní virtuální adresu.</span><span class="sxs-lookup"><span data-stu-id="61929-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="61929-108">[out] Ukazatel rámec počáteční relativní virtuální adresa.</span><span class="sxs-lookup"><span data-stu-id="61929-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61929-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="61929-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61929-110">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="61929-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61929-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="61929-111">Requirements</span></span>  
 <span data-ttu-id="61929-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61929-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61929-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61929-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61929-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61929-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61929-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61929-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61929-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61929-116">See also</span></span>
- [<span data-ttu-id="61929-117">ICorDebugSymbolProvider2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61929-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="61929-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="61929-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
