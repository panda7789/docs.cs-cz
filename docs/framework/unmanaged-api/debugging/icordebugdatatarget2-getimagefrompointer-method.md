---
title: ICorDebugDataTarget2::GetImageFromPointer – metoda
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
ms.openlocfilehash: 3ac1f8ab98583357a3aa622b5032d9ae121ebdf2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178921"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="ccd70-102">ICorDebugDataTarget2::GetImageFromPointer – metoda</span><span class="sxs-lookup"><span data-stu-id="ccd70-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="ccd70-103">Vrátí základní adresu a velikost modulu z adresy v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="ccd70-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccd70-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccd70-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,
   [out] CORDB_ADDRESS *pImageBase,
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccd70-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ccd70-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="ccd70-106">Hodnota [CORDB_ADDRESS,](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) která představuje adresu v modulu.</span><span class="sxs-lookup"><span data-stu-id="ccd70-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="ccd70-107">[out] Hodnota [CORDB_ADDRESS,](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) která představuje základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="ccd70-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="ccd70-108">Ukazatel na velikost modulu.</span><span class="sxs-lookup"><span data-stu-id="ccd70-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccd70-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ccd70-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ccd70-110">Tato metoda je k dispozici pouze s nativní .NET.</span><span class="sxs-lookup"><span data-stu-id="ccd70-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccd70-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ccd70-111">Requirements</span></span>  
 <span data-ttu-id="ccd70-112">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccd70-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccd70-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ccd70-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ccd70-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ccd70-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ccd70-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccd70-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccd70-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccd70-116">See also</span></span>

- [<span data-ttu-id="ccd70-117">ICorDebugDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ccd70-117">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="ccd70-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ccd70-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
