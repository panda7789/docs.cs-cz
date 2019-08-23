---
title: 'ICorDebugMergedAssemblyRecord:: GetPublicKey – metoda'
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e08b1edcef3e93caa82be3a4342c6a0264734bea
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940020"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="79461-102">ICorDebugMergedAssemblyRecord:: GetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="79461-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="79461-103">Získá veřejný klíč sestavení.</span><span class="sxs-lookup"><span data-stu-id="79461-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79461-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79461-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79461-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="79461-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="79461-106">pro Maximální počet bajtů v `pbPublicKey` poli.</span><span class="sxs-lookup"><span data-stu-id="79461-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="79461-107">mimo Ukazatel na skutečný počet bajtů zapsaných do `pbPublicKey` pole.</span><span class="sxs-lookup"><span data-stu-id="79461-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="79461-108">mimo Ukazatel na pole bajtů, které obsahuje veřejný klíč sestavení.</span><span class="sxs-lookup"><span data-stu-id="79461-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79461-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79461-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79461-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="79461-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79461-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="79461-111">Requirements</span></span>  
 <span data-ttu-id="79461-112">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79461-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79461-113">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="79461-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79461-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79461-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79461-115">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79461-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79461-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79461-116">See also</span></span>

- [<span data-ttu-id="79461-117">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="79461-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="79461-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="79461-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
