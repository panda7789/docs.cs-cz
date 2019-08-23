---
title: 'ICorDebugMergedAssemblyRecord:: GetPublicKeyToken – metoda'
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 626aa53740839df0b47a876b3e82814a63ffd82d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936856"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="55db1-102">ICorDebugMergedAssemblyRecord:: GetPublicKeyToken – metoda</span><span class="sxs-lookup"><span data-stu-id="55db1-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>
<span data-ttu-id="55db1-103">Získá token veřejného klíče sestavení.</span><span class="sxs-lookup"><span data-stu-id="55db1-103">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55db1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55db1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55db1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="55db1-105">Parameters</span></span>  
 `cbPublicKeyToken`  
 <span data-ttu-id="55db1-106">pro Maximální počet bajtů v `pbPublicKeyToken` poli.</span><span class="sxs-lookup"><span data-stu-id="55db1-106">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="55db1-107">mimo Ukazatel na skutečný počet bajtů zapsaných do `pbPublicKeyToken` pole.</span><span class="sxs-lookup"><span data-stu-id="55db1-107">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="55db1-108">mimo Ukazatel na pole bajtů, které obsahuje token veřejného klíče sestavení.</span><span class="sxs-lookup"><span data-stu-id="55db1-108">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55db1-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="55db1-109">Remarks</span></span>  
 <span data-ttu-id="55db1-110">Token veřejného klíče sestavení je posledních osm bajtů hodnoty hash SHA1 svého veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="55db1-110">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55db1-111">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="55db1-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55db1-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="55db1-112">Requirements</span></span>  
 <span data-ttu-id="55db1-113">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55db1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55db1-114">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="55db1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55db1-115">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55db1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55db1-116">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55db1-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55db1-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55db1-117">See also</span></span>

- [<span data-ttu-id="55db1-118">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="55db1-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="55db1-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="55db1-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
