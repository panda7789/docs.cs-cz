---
title: ICorDebugMergedAssemblyRecord::Metoda GetPublicKeyToken
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
ms.openlocfilehash: 79df5c3e8b07879a26272f595664abab011101bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178726"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="8007d-102">ICorDebugMergedAssemblyRecord::Metoda GetPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="8007d-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>
<span data-ttu-id="8007d-103">Získá token veřejného klíče sestavení.</span><span class="sxs-lookup"><span data-stu-id="8007d-103">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8007d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8007d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,
   [out] ULONG32 *pcbPublicKeyToken,
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8007d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8007d-105">Parameters</span></span>  
 `cbPublicKeyToken`  
 <span data-ttu-id="8007d-106">[v] Maximální počet bajtů v `pbPublicKeyToken` poli.</span><span class="sxs-lookup"><span data-stu-id="8007d-106">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="8007d-107">[out] Ukazatel na skutečný počet bajtů zapsaných do `pbPublicKeyToken` pole.</span><span class="sxs-lookup"><span data-stu-id="8007d-107">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="8007d-108">[out] Ukazatel na bajtové pole, které obsahuje token veřejného klíče sestavení.</span><span class="sxs-lookup"><span data-stu-id="8007d-108">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8007d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8007d-109">Remarks</span></span>  
 <span data-ttu-id="8007d-110">Token veřejného klíče sestavení je posledních osm bajtů sha1 hash jeho veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="8007d-110">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8007d-111">Tato metoda je k dispozici pouze s nativní .NET.</span><span class="sxs-lookup"><span data-stu-id="8007d-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8007d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8007d-112">Requirements</span></span>  
 <span data-ttu-id="8007d-113">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8007d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8007d-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8007d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8007d-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8007d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8007d-116">**Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8007d-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8007d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="8007d-117">See also</span></span>

- [<span data-ttu-id="8007d-118">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8007d-118">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="8007d-119">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8007d-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
