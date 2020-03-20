---
title: ICorDebugMergedAssemblyRecord::Metoda GetPublicKey
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: 632e990899346493d5a7df08d293e25b83ed7ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178730"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="5587b-102">ICorDebugMergedAssemblyRecord::Metoda GetPublicKey</span><span class="sxs-lookup"><span data-stu-id="5587b-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="5587b-103">Získá veřejného klíče sestavení.</span><span class="sxs-lookup"><span data-stu-id="5587b-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5587b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5587b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,
   [out] ULONG32 *pcbPublicKey,
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5587b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5587b-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="5587b-106">[v] Maximální počet bajtů v `pbPublicKey` poli.</span><span class="sxs-lookup"><span data-stu-id="5587b-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="5587b-107">[out] Ukazatel na skutečný počet bajtů zapsaných do `pbPublicKey` pole.</span><span class="sxs-lookup"><span data-stu-id="5587b-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="5587b-108">[out] Ukazatel na bajtové pole, které obsahuje veřejný klíč sestavení.</span><span class="sxs-lookup"><span data-stu-id="5587b-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5587b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5587b-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5587b-110">Tato metoda je k dispozici pouze s nativní .NET.</span><span class="sxs-lookup"><span data-stu-id="5587b-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5587b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5587b-111">Requirements</span></span>  
 <span data-ttu-id="5587b-112">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5587b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5587b-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5587b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5587b-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5587b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5587b-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5587b-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5587b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="5587b-116">See also</span></span>

- [<span data-ttu-id="5587b-117">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5587b-117">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="5587b-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5587b-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
