---
title: ICorDebugType2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
ms.openlocfilehash: e90952a92c408762a98a2bfcb91b6aeb72052df1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791219"
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="04774-102">ICorDebugType2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04774-102">ICorDebugType2 Interface</span></span>
<span data-ttu-id="04774-103">Rozšiřuje rozhraní ICorDebugType, aby získal identifikátor typu základního typu nebo komplexního (uživatelsky definovaného) typu.</span><span class="sxs-lookup"><span data-stu-id="04774-103">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="04774-104">Metody</span><span class="sxs-lookup"><span data-stu-id="04774-104">Methods</span></span>  
  
|<span data-ttu-id="04774-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="04774-105">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="04774-106">GetTypeID – metoda</span><span class="sxs-lookup"><span data-stu-id="04774-106">GetTypeID Method</span></span>](icordebugtype2-gettypeid-method.md)|<span data-ttu-id="04774-107">Získá [COR_TYPEID](cor-typeid-structure.md) pro tento typ.</span><span class="sxs-lookup"><span data-stu-id="04774-107">Gets a [COR_TYPEID](cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04774-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04774-108">Remarks</span></span>  
 <span data-ttu-id="04774-109">Toto rozhraní je logickou příponou rozhraní ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="04774-109">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04774-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="04774-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04774-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="04774-111">Example</span></span>  
 <span data-ttu-id="04774-112">Následující fragment kódu ukazuje použití metody [ICorDebugType2:: GetTypeId.](icordebugtype2-gettypeid-method.md) .</span><span class="sxs-lookup"><span data-stu-id="04774-112">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```cpp  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="04774-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04774-113">Requirements</span></span>  
 <span data-ttu-id="04774-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04774-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04774-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="04774-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04774-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="04774-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04774-117">**Verze .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04774-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04774-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04774-118">See also</span></span>

- [<span data-ttu-id="04774-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="04774-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
