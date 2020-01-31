---
title: ICorDebugDataTarget2::GetImageLocation – metoda
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
ms.openlocfilehash: ba1cc8c91c53547c6ed4025ee67a69e253f3596d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783584"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="fd3f1-102">ICorDebugDataTarget2::GetImageLocation – metoda</span><span class="sxs-lookup"><span data-stu-id="fd3f1-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>
<span data-ttu-id="fd3f1-103">Vrátí cestu modulu ze základní adresy modulu.</span><span class="sxs-lookup"><span data-stu-id="fd3f1-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd3f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd3f1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd3f1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fd3f1-105">Parameters</span></span>  
 `baseAddress`  
 <span data-ttu-id="fd3f1-106">pro Hodnota [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) , která představuje základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="fd3f1-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="fd3f1-107">pro Počet znaků ve vyrovnávací paměti, který má přijmout cestu modulu.</span><span class="sxs-lookup"><span data-stu-id="fd3f1-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="fd3f1-108">mimo Ukazatel na počet znaků zapsaných do vyrovnávací paměti `szName`.</span><span class="sxs-lookup"><span data-stu-id="fd3f1-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="fd3f1-109">mimo Cesta k modulu</span><span class="sxs-lookup"><span data-stu-id="fd3f1-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd3f1-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fd3f1-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fd3f1-111">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fd3f1-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd3f1-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fd3f1-112">Requirements</span></span>  
 <span data-ttu-id="fd3f1-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd3f1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd3f1-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fd3f1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd3f1-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fd3f1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd3f1-116">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd3f1-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd3f1-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd3f1-117">See also</span></span>

- [<span data-ttu-id="fd3f1-118">ICorDebugDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fd3f1-118">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="fd3f1-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="fd3f1-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
