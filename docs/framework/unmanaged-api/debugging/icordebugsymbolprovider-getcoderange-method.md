---
title: 'ICorDebugSymbolProvider:: GetCodeRange – metoda'
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
ms.openlocfilehash: dbe042641cadae182efac30502a70631be359bbe
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791641"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="eaee2-102">ICorDebugSymbolProvider:: GetCodeRange – metoda</span><span class="sxs-lookup"><span data-stu-id="eaee2-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="eaee2-103">Získá počáteční adresu a velikost metody dané relativní virtuální adresy (RVA) v metodě.</span><span class="sxs-lookup"><span data-stu-id="eaee2-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaee2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eaee2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eaee2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eaee2-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="eaee2-106">pro Relativní virtuální adresa (RVA) v metodě.</span><span class="sxs-lookup"><span data-stu-id="eaee2-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="eaee2-107">mimo Ukazatel na počáteční adresu metody.</span><span class="sxs-lookup"><span data-stu-id="eaee2-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="eaee2-108">Ukazatel na velikost kódu metody (počet bajtů kódu metody).</span><span class="sxs-lookup"><span data-stu-id="eaee2-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eaee2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eaee2-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eaee2-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="eaee2-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaee2-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eaee2-111">Requirements</span></span>  
 <span data-ttu-id="eaee2-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eaee2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaee2-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="eaee2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eaee2-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="eaee2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eaee2-115">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaee2-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaee2-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eaee2-116">See also</span></span>

- [<span data-ttu-id="eaee2-117">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eaee2-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="eaee2-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="eaee2-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
