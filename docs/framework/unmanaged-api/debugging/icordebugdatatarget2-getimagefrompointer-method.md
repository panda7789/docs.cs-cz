---
title: ICorDebugDataTarget2::GetImageFromPointer – metoda
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5dab9183075f563f52a4fc982eda5cb172556554
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154372"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="d19be-102">ICorDebugDataTarget2::GetImageFromPointer – metoda</span><span class="sxs-lookup"><span data-stu-id="d19be-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="d19be-103">Vrátí základní adresa modulu a velikost z adresy v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="d19be-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d19be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d19be-104">Syntax</span></span>  
  
```  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d19be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d19be-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="d19be-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) hodnota představující adresu v modulu.</span><span class="sxs-lookup"><span data-stu-id="d19be-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="d19be-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) hodnotu, která představuje základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="d19be-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="d19be-108">Ukazatel na velikost modulu.</span><span class="sxs-lookup"><span data-stu-id="d19be-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d19be-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d19be-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d19be-110">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d19be-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d19be-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d19be-111">Requirements</span></span>  
 <span data-ttu-id="d19be-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d19be-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d19be-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d19be-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d19be-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d19be-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d19be-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d19be-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d19be-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d19be-116">See also</span></span>

- [<span data-ttu-id="d19be-117">Rozhraní ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="d19be-117">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="d19be-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d19be-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
