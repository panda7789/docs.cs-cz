---
title: ICorDebugMergedAssemblyRecord::GetPublicKeyToken – metoda
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cc02c1f69235403e2f5df28168e17a70f183682
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762410"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="c827a-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken – metoda</span><span class="sxs-lookup"><span data-stu-id="c827a-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>
<span data-ttu-id="c827a-103">Získá token veřejného klíče sestavení.</span><span class="sxs-lookup"><span data-stu-id="c827a-103">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c827a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c827a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c827a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c827a-105">Parameters</span></span>  
 `cbPublicKeyToken`  
 <span data-ttu-id="c827a-106">[in] Maximální počet bajtů `pbPublicKeyToken` pole.</span><span class="sxs-lookup"><span data-stu-id="c827a-106">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="c827a-107">[out] Ukazatel na skutečný počet bajtů zapsaný na `pbPublicKeyToken` pole.</span><span class="sxs-lookup"><span data-stu-id="c827a-107">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="c827a-108">[out] Ukazatel na bajtové pole, který obsahuje token veřejného klíče sestavení.</span><span class="sxs-lookup"><span data-stu-id="c827a-108">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c827a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c827a-109">Remarks</span></span>  
 <span data-ttu-id="c827a-110">Token veřejného klíče sestavení je posledních osm bajtů hash SHA1 svůj veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="c827a-110">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c827a-111">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c827a-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c827a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c827a-112">Requirements</span></span>  
 <span data-ttu-id="c827a-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c827a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c827a-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c827a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c827a-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c827a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c827a-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c827a-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c827a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c827a-117">See also</span></span>

- [<span data-ttu-id="c827a-118">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c827a-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="c827a-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c827a-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
