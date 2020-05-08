---
title: ICorDebugDataTarget2::GetImageLocation – metoda
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
ms.openlocfilehash: 185b6a4979491a323f6eb15ab08a06f87fabc8d3
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976457"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="c79b2-102">ICorDebugDataTarget2::GetImageLocation – metoda</span><span class="sxs-lookup"><span data-stu-id="c79b2-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>
<span data-ttu-id="c79b2-103">Vrátí cestu modulu ze základní adresy modulu.</span><span class="sxs-lookup"><span data-stu-id="c79b2-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c79b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c79b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c79b2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c79b2-105">Parameters</span></span>  
 `baseAddress`  
 <span data-ttu-id="c79b2-106">pro Hodnota [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) , která představuje základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="c79b2-106">[in] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c79b2-107">pro Počet znaků ve vyrovnávací paměti, který má přijmout cestu modulu.</span><span class="sxs-lookup"><span data-stu-id="c79b2-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c79b2-108">mimo Ukazatel na počet znaků zapsaných do `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="c79b2-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="c79b2-109">mimo Cesta k modulu</span><span class="sxs-lookup"><span data-stu-id="c79b2-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c79b2-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c79b2-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c79b2-111">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c79b2-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c79b2-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c79b2-112">Requirements</span></span>  
 <span data-ttu-id="c79b2-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c79b2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c79b2-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c79b2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c79b2-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c79b2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c79b2-116">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c79b2-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c79b2-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="c79b2-117">See also</span></span>

- [<span data-ttu-id="c79b2-118">Rozhraní ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="c79b2-118">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="c79b2-119">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c79b2-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
