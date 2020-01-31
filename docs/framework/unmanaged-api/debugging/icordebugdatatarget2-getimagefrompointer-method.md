---
title: ICorDebugDataTarget2::GetImageFromPointer – metoda
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
ms.openlocfilehash: 55c87731399cf1e7a6747720b8bb33de7e01906c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788833"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="cb14e-102">ICorDebugDataTarget2::GetImageFromPointer – metoda</span><span class="sxs-lookup"><span data-stu-id="cb14e-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="cb14e-103">Vrátí základní adresu modulu a velikost z adresy v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="cb14e-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb14e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb14e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb14e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb14e-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="cb14e-106">Hodnota [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) , která představuje adresu v modulu.</span><span class="sxs-lookup"><span data-stu-id="cb14e-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="cb14e-107">mimo Hodnota [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) , která představuje základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="cb14e-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="cb14e-108">Ukazatel na velikost modulu.</span><span class="sxs-lookup"><span data-stu-id="cb14e-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb14e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb14e-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb14e-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cb14e-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb14e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb14e-111">Requirements</span></span>  
 <span data-ttu-id="cb14e-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb14e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb14e-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cb14e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb14e-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cb14e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb14e-115">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb14e-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb14e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb14e-116">See also</span></span>

- [<span data-ttu-id="cb14e-117">ICorDebugDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb14e-117">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="cb14e-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="cb14e-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
