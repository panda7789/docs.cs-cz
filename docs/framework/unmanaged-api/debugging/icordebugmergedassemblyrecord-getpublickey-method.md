---
title: 'ICorDebugMergedAssemblyRecord:: GetPublicKey – metoda'
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: c8c6e9adcb9d29f5e234dd1b8dfd351fac575301
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793120"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="e22cd-102">ICorDebugMergedAssemblyRecord:: GetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="e22cd-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="e22cd-103">Získá veřejný klíč sestavení.</span><span class="sxs-lookup"><span data-stu-id="e22cd-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e22cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e22cd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e22cd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e22cd-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="e22cd-106">pro Maximální počet bajtů v poli `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="e22cd-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="e22cd-107">mimo Ukazatel na skutečný počet bajtů zapsaných do pole `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="e22cd-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="e22cd-108">mimo Ukazatel na pole bajtů, které obsahuje veřejný klíč sestavení.</span><span class="sxs-lookup"><span data-stu-id="e22cd-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e22cd-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e22cd-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e22cd-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e22cd-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e22cd-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e22cd-111">Requirements</span></span>  
 <span data-ttu-id="e22cd-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e22cd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e22cd-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e22cd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e22cd-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e22cd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e22cd-115">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e22cd-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e22cd-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e22cd-116">See also</span></span>

- [<span data-ttu-id="e22cd-117">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e22cd-117">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="e22cd-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e22cd-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
