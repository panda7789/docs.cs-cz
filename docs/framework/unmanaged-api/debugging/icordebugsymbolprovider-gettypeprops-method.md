---
title: 'ICorDebugSymbolProvider:: GetTypeProps – metoda'
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
ms.openlocfilehash: 5fa091eaf2cf93b0c645effeec3c959d42665fc9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791546"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="2e1f9-102">ICorDebugSymbolProvider:: GetTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="2e1f9-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>
<span data-ttu-id="2e1f9-103">Vrátí informace o vlastnostech typu, jako je například počet podpisů svých obecných parametrů, s ohledem na relativní virtuální adresu (RVA) v tabulce vtable.</span><span class="sxs-lookup"><span data-stu-id="2e1f9-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e1f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e1f9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e1f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e1f9-105">Parameters</span></span>  
 `tableRva`  
 <span data-ttu-id="2e1f9-106">pro Relativní virtuální adresa (RVA) v tabulce vtable.</span><span class="sxs-lookup"><span data-stu-id="2e1f9-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="2e1f9-107">pro Velikost pole `signature`.</span><span class="sxs-lookup"><span data-stu-id="2e1f9-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="2e1f9-108">Viz část poznámky.</span><span class="sxs-lookup"><span data-stu-id="2e1f9-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="2e1f9-109">mimo mimo Ukazatel na velikost vráceného pole `signature`.</span><span class="sxs-lookup"><span data-stu-id="2e1f9-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="2e1f9-110">mimo Vyrovnávací paměť, která obsahuje token TypeSpec podpisy všech obecných parametrů.</span><span class="sxs-lookup"><span data-stu-id="2e1f9-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e1f9-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2e1f9-111">Remarks</span></span>  
 <span data-ttu-id="2e1f9-112">Chcete-li získat požadovanou velikost `signature` pole typu, nastavte argument `cbSignature` na hodnotu 0 a `signature` na **hodnotu null**.</span><span class="sxs-lookup"><span data-stu-id="2e1f9-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="2e1f9-113">Když se metoda vrátí, `pcbSignature` bude obsahovat počet bajtů vyžadovaných pro pole `signature`.</span><span class="sxs-lookup"><span data-stu-id="2e1f9-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2e1f9-114">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2e1f9-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e1f9-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e1f9-115">Requirements</span></span>  
 <span data-ttu-id="2e1f9-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e1f9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e1f9-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2e1f9-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e1f9-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2e1f9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e1f9-119">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e1f9-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e1f9-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e1f9-120">See also</span></span>

- [<span data-ttu-id="2e1f9-121">GetMethodProps – metoda</span><span class="sxs-lookup"><span data-stu-id="2e1f9-121">GetMethodProps Method</span></span>](icordebugsymbolprovider-getmethodprops-method.md)
- [<span data-ttu-id="2e1f9-122">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e1f9-122">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="2e1f9-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2e1f9-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
