---
title: "ICorDebugSymbolProvider2::GetFrameProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3892b8da3286132709792513f055d6ce75bd3fce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="71d0f-102">ICorDebugSymbolProvider2::GetFrameProps – metoda</span><span class="sxs-lookup"><span data-stu-id="71d0f-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="71d0f-103">Vrátí metodu počáteční relativní virtuální adresa metodu a nadřazeného rámce zadaný relativní virtuální adresu kódu.</span><span class="sxs-lookup"><span data-stu-id="71d0f-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71d0f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71d0f-104">Syntax</span></span>  
  
```  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="71d0f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="71d0f-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="71d0f-106">[v] Kód relativní virtuální adresu.</span><span class="sxs-lookup"><span data-stu-id="71d0f-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="71d0f-107">[out] Ukazatel metoda počáteční relativní virtuální adresa.</span><span class="sxs-lookup"><span data-stu-id="71d0f-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="71d0f-108">[out] Ukazatel na rámečku počáteční relativní virtuální adresa.</span><span class="sxs-lookup"><span data-stu-id="71d0f-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71d0f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="71d0f-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71d0f-110">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="71d0f-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71d0f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="71d0f-111">Requirements</span></span>  
 <span data-ttu-id="71d0f-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71d0f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71d0f-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71d0f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71d0f-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71d0f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71d0f-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71d0f-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71d0f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="71d0f-116">See Also</span></span>  
 [<span data-ttu-id="71d0f-117">ICorDebugSymbolProvider2 rozhraní</span><span class="sxs-lookup"><span data-stu-id="71d0f-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [<span data-ttu-id="71d0f-118">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="71d0f-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
