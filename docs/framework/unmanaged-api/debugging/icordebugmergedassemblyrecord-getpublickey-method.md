---
title: 'ICorDebugMergedAssemblyRecord:: GetPublicKey – metoda'
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: 51724aa1ee6101c50c7cdb4b6071fb458814f483
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213540"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="12ce1-102">ICorDebugMergedAssemblyRecord:: GetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="12ce1-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="12ce1-103">Získá veřejný klíč sestavení.</span><span class="sxs-lookup"><span data-stu-id="12ce1-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12ce1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12ce1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,
   [out] ULONG32 *pcbPublicKey,
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12ce1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="12ce1-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="12ce1-106">pro Maximální počet bajtů v `pbPublicKey` poli.</span><span class="sxs-lookup"><span data-stu-id="12ce1-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="12ce1-107">mimo Ukazatel na skutečný počet bajtů zapsaných do `pbPublicKey` pole.</span><span class="sxs-lookup"><span data-stu-id="12ce1-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="12ce1-108">mimo Ukazatel na pole bajtů, které obsahuje veřejný klíč sestavení.</span><span class="sxs-lookup"><span data-stu-id="12ce1-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12ce1-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12ce1-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12ce1-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="12ce1-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12ce1-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12ce1-111">Requirements</span></span>  
 <span data-ttu-id="12ce1-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12ce1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12ce1-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="12ce1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12ce1-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="12ce1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12ce1-115">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12ce1-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12ce1-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="12ce1-116">See also</span></span>

- [<span data-ttu-id="12ce1-117">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12ce1-117">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="12ce1-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12ce1-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
