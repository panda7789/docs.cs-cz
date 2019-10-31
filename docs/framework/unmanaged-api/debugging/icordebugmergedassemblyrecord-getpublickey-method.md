---
title: 'ICorDebugMergedAssemblyRecord:: GetPublicKey – metoda'
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: 9cf5f6b6d12303b3f59588c5fb663c457da79cb9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131398"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="ab1f2-102">ICorDebugMergedAssemblyRecord:: GetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="ab1f2-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="ab1f2-103">Získá veřejný klíč sestavení.</span><span class="sxs-lookup"><span data-stu-id="ab1f2-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab1f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab1f2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab1f2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab1f2-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="ab1f2-106">pro Maximální počet bajtů v poli `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="ab1f2-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="ab1f2-107">mimo Ukazatel na skutečný počet bajtů zapsaných do pole `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="ab1f2-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="ab1f2-108">mimo Ukazatel na pole bajtů, které obsahuje veřejný klíč sestavení.</span><span class="sxs-lookup"><span data-stu-id="ab1f2-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab1f2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab1f2-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab1f2-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ab1f2-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab1f2-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ab1f2-111">Requirements</span></span>  
 <span data-ttu-id="ab1f2-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab1f2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab1f2-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ab1f2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab1f2-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ab1f2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab1f2-115">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab1f2-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab1f2-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab1f2-116">See also</span></span>

- [<span data-ttu-id="ab1f2-117">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab1f2-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="ab1f2-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ab1f2-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
