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
ms.openlocfilehash: 7d379f0df70690501920a9ba5b40d560b10a7cb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="c051d-102">ICorDebugMergedAssemblyRecord::GetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="c051d-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="c051d-103">Získá sestavení veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="c051d-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c051d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c051d-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c051d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c051d-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="c051d-106">[v] Maximální počet bajtů `pbPublicKey` pole.</span><span class="sxs-lookup"><span data-stu-id="c051d-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="c051d-107">[out] Ukazatel na skutečný počet bajtů zapsaných do `pbPublicKey` pole.</span><span class="sxs-lookup"><span data-stu-id="c051d-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="c051d-108">[out] Ukazatel na bajtové pole obsahující veřejný klíč je sestavení.</span><span class="sxs-lookup"><span data-stu-id="c051d-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c051d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c051d-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c051d-110">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="c051d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c051d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c051d-111">Requirements</span></span>  
 <span data-ttu-id="c051d-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c051d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c051d-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c051d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c051d-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c051d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c051d-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c051d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c051d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c051d-116">See Also</span></span>  
 [<span data-ttu-id="c051d-117">ICorDebugMergedAssemblyRecord rozhraní</span><span class="sxs-lookup"><span data-stu-id="c051d-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="c051d-118">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="c051d-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
