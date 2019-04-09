---
title: Metoda ICorDebugLoadedModule::GetName
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9bf09c01d24315c3f239911326f1844a0b2cc101
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111264"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="04a23-102">Metoda ICorDebugLoadedModule::GetName</span><span class="sxs-lookup"><span data-stu-id="04a23-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="04a23-103">Získá název načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="04a23-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04a23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04a23-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04a23-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04a23-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="04a23-106">[in] Počet znaků `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="04a23-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="04a23-107">[out] Ukazatel na počet aktuálně zapsaných do znaků `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="04a23-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="04a23-108">[out] Pole znaků, které obsahují název načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="04a23-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04a23-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04a23-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04a23-110">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="04a23-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04a23-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04a23-111">Requirements</span></span>  
 <span data-ttu-id="04a23-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04a23-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04a23-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04a23-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04a23-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04a23-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="04a23-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="04a23-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="04a23-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04a23-116">See also</span></span>

- [<span data-ttu-id="04a23-117">Rozhraní ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="04a23-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="04a23-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04a23-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
