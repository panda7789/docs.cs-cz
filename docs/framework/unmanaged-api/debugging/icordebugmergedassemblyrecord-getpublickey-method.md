---
title: ICorDebugMergedAssemblyRecord::GetPublicKey – metoda
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 610e46d5cb550a266c5558c49239d1818c1e85de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107273"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="bcf3f-102">ICorDebugMergedAssemblyRecord::GetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="bcf3f-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="bcf3f-103">Získá veřejný klíč sestavení.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcf3f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcf3f-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcf3f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bcf3f-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="bcf3f-106">[in] Maximální počet bajtů `pbPublicKey` pole.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="bcf3f-107">[out] Ukazatel na skutečný počet bajtů zapsaný na `pbPublicKey` pole.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="bcf3f-108">[out] Ukazatel na bajtové pole obsahující veřejný klíč sestavení.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcf3f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bcf3f-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bcf3f-110">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcf3f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bcf3f-111">Requirements</span></span>  
 <span data-ttu-id="bcf3f-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcf3f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcf3f-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bcf3f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bcf3f-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bcf3f-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="bcf3f-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="bcf3f-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bcf3f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bcf3f-116">See also</span></span>

- [<span data-ttu-id="bcf3f-117">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bcf3f-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="bcf3f-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bcf3f-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
