---
title: "ICorDebugMergedAssemblyRecord::GetPublicKeyToken – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c286981def6f12f8e5b8fa5397f23535d4d4623
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="7d638-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken – metoda</span><span class="sxs-lookup"><span data-stu-id="7d638-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>
<span data-ttu-id="7d638-103">Získá token veřejného klíče je sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d638-103">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d638-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d638-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d638-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d638-105">Parameters</span></span>  
 `cbPublicKeyToken`  
 <span data-ttu-id="7d638-106">[v] Maximální počet bajtů `pbPublicKeyToken` pole.</span><span class="sxs-lookup"><span data-stu-id="7d638-106">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="7d638-107">[out] Ukazatel na skutečný počet bajtů zapsaných do `pbPublicKeyToken` pole.</span><span class="sxs-lookup"><span data-stu-id="7d638-107">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="7d638-108">[out] Ukazatel na bajtové pole, která obsahuje toto sestavení tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="7d638-108">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d638-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d638-109">Remarks</span></span>  
 <span data-ttu-id="7d638-110">Token veřejného klíče sestavení je poslední osm bajtů algoritmus hash SHA1 svůj veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="7d638-110">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d638-111">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="7d638-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d638-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d638-112">Requirements</span></span>  
 <span data-ttu-id="7d638-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d638-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d638-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d638-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d638-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d638-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d638-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d638-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d638-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d638-117">See Also</span></span>  
 [<span data-ttu-id="7d638-118">ICorDebugMergedAssemblyRecord rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d638-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="7d638-119">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d638-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
