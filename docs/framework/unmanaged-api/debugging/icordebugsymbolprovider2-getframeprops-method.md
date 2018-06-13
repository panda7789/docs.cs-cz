---
title: ICorDebugSymbolProvider2::GetFrameProps – metoda
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 419e7bae5998679fafac48ebfd5b0673e0e4bac5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419078"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="ce59d-102">ICorDebugSymbolProvider2::GetFrameProps – metoda</span><span class="sxs-lookup"><span data-stu-id="ce59d-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="ce59d-103">Vrátí metodu počáteční relativní virtuální adresa metodu a nadřazeného rámce zadaný relativní virtuální adresu kódu.</span><span class="sxs-lookup"><span data-stu-id="ce59d-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce59d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce59d-104">Syntax</span></span>  
  
```  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ce59d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce59d-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="ce59d-106">[v] Kód relativní virtuální adresu.</span><span class="sxs-lookup"><span data-stu-id="ce59d-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="ce59d-107">[out] Ukazatel metoda počáteční relativní virtuální adresa.</span><span class="sxs-lookup"><span data-stu-id="ce59d-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="ce59d-108">[out] Ukazatel na rámečku počáteční relativní virtuální adresa.</span><span class="sxs-lookup"><span data-stu-id="ce59d-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce59d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ce59d-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce59d-110">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="ce59d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce59d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ce59d-111">Requirements</span></span>  
 <span data-ttu-id="ce59d-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce59d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce59d-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce59d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce59d-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce59d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce59d-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce59d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce59d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce59d-116">See Also</span></span>  
 [<span data-ttu-id="ce59d-117">ICorDebugSymbolProvider2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ce59d-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [<span data-ttu-id="ce59d-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ce59d-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
