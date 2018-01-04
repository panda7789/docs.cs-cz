---
title: "ICorDebugMergedAssemblyRecord::GetPublicKey – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a47eb051cd9922b8640b8b612ff0ac5882b6a8ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="96506-102">ICorDebugMergedAssemblyRecord::GetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="96506-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="96506-103">Získá sestavení veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="96506-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96506-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96506-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="96506-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96506-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="96506-106">[v] Maximální počet bajtů `pbPublicKey` pole.</span><span class="sxs-lookup"><span data-stu-id="96506-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="96506-107">[out] Ukazatel na skutečný počet bajtů zapsaných do `pbPublicKey` pole.</span><span class="sxs-lookup"><span data-stu-id="96506-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="96506-108">[out] Ukazatel na bajtové pole obsahující veřejný klíč je sestavení.</span><span class="sxs-lookup"><span data-stu-id="96506-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96506-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96506-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96506-110">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="96506-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96506-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="96506-111">Requirements</span></span>  
 <span data-ttu-id="96506-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96506-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96506-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96506-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96506-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96506-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96506-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96506-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96506-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="96506-116">See Also</span></span>  
 [<span data-ttu-id="96506-117">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96506-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="96506-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="96506-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
