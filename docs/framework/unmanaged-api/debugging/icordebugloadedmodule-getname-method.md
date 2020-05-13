---
title: Metoda ICorDebugLoadedModule::GetName
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
ms.openlocfilehash: 4a0c4e99f23dc949b0bbaa8bbda35cff1537cf3c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209861"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="ff38f-102">Metoda ICorDebugLoadedModule::GetName</span><span class="sxs-lookup"><span data-stu-id="ff38f-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="ff38f-103">Získá název načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="ff38f-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff38f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff38f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff38f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff38f-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ff38f-106">pro Počet znaků ve `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ff38f-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ff38f-107">mimo Ukazatel na počet znaků skutečně zapsaných do `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ff38f-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="ff38f-108">mimo Pole znaků, které obsahují název načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="ff38f-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff38f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff38f-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff38f-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ff38f-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff38f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff38f-111">Requirements</span></span>  
 <span data-ttu-id="ff38f-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff38f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff38f-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ff38f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff38f-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ff38f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff38f-115">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff38f-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff38f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff38f-116">See also</span></span>

- [<span data-ttu-id="ff38f-117">Rozhraní ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="ff38f-117">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="ff38f-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff38f-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
