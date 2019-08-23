---
title: 'ICorDebugSymbolProvider:: GetCodeRange – metoda'
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18fd8fdf9bcfa20b686ad1f04cd8dcc3b1c26de2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964645"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="b4364-102">ICorDebugSymbolProvider:: GetCodeRange – metoda</span><span class="sxs-lookup"><span data-stu-id="b4364-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="b4364-103">Získá počáteční adresu a velikost metody dané relativní virtuální adresy (RVA) v metodě.</span><span class="sxs-lookup"><span data-stu-id="b4364-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4364-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4364-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4364-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4364-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="b4364-106">pro Relativní virtuální adresa (RVA) v metodě.</span><span class="sxs-lookup"><span data-stu-id="b4364-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="b4364-107">mimo Ukazatel na počáteční adresu metody.</span><span class="sxs-lookup"><span data-stu-id="b4364-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="b4364-108">Ukazatel na velikost kódu metody (počet bajtů kódu metody).</span><span class="sxs-lookup"><span data-stu-id="b4364-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4364-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4364-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4364-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b4364-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4364-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b4364-111">Requirements</span></span>  
 <span data-ttu-id="b4364-112">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4364-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4364-113">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b4364-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4364-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4364-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4364-115">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4364-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4364-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4364-116">See also</span></span>

- [<span data-ttu-id="b4364-117">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4364-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="b4364-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b4364-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
