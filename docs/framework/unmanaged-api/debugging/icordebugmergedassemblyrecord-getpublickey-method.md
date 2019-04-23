---
title: ICorDebugMergedAssemblyRecord::GetPublicKey – metoda
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 610e46d5cb550a266c5558c49239d1818c1e85de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107273"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="01ae6-102">ICorDebugMergedAssemblyRecord::GetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="01ae6-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="01ae6-103">Získá veřejný klíč sestavení.</span><span class="sxs-lookup"><span data-stu-id="01ae6-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01ae6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01ae6-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01ae6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01ae6-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="01ae6-106">[in] Maximální počet bajtů `pbPublicKey` pole.</span><span class="sxs-lookup"><span data-stu-id="01ae6-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="01ae6-107">[out] Ukazatel na skutečný počet bajtů zapsaný na `pbPublicKey` pole.</span><span class="sxs-lookup"><span data-stu-id="01ae6-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="01ae6-108">[out] Ukazatel na bajtové pole obsahující veřejný klíč sestavení.</span><span class="sxs-lookup"><span data-stu-id="01ae6-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01ae6-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01ae6-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01ae6-110">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="01ae6-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01ae6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01ae6-111">Requirements</span></span>  
 <span data-ttu-id="01ae6-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01ae6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01ae6-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01ae6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01ae6-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01ae6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01ae6-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01ae6-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01ae6-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01ae6-116">See also</span></span>

- [<span data-ttu-id="01ae6-117">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01ae6-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="01ae6-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="01ae6-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
