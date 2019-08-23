---
title: 'ICorDebugSymbolProvider:: GetTypeProps – metoda'
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c8ea3a201cc94ef7bdf679371ef43ab2641b791
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955558"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="50cac-102">ICorDebugSymbolProvider:: GetTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="50cac-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>
<span data-ttu-id="50cac-103">Vrátí informace o vlastnostech typu, jako je například počet podpisů svých obecných parametrů, s ohledem na relativní virtuální adresu (RVA) v tabulce vtable.</span><span class="sxs-lookup"><span data-stu-id="50cac-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50cac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50cac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50cac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="50cac-105">Parameters</span></span>  
 `tableRva`  
 <span data-ttu-id="50cac-106">pro Relativní virtuální adresa (RVA) v tabulce vtable.</span><span class="sxs-lookup"><span data-stu-id="50cac-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="50cac-107">pro Velikost `signature` pole.</span><span class="sxs-lookup"><span data-stu-id="50cac-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="50cac-108">Viz část poznámky.</span><span class="sxs-lookup"><span data-stu-id="50cac-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="50cac-109">mimo mimo Ukazatel na velikost vráceného `signature` pole.</span><span class="sxs-lookup"><span data-stu-id="50cac-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="50cac-110">mimo Vyrovnávací paměť, která obsahuje token TypeSpec podpisy všech obecných parametrů.</span><span class="sxs-lookup"><span data-stu-id="50cac-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50cac-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="50cac-111">Remarks</span></span>  
 <span data-ttu-id="50cac-112">Chcete- `signature` li získat požadovanou velikost pole typu, `cbSignature` nastavte argument na hodnotu 0 a `signature` na **hodnotu null**.</span><span class="sxs-lookup"><span data-stu-id="50cac-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="50cac-113">Když se metoda vrátí, `pcbSignature` bude obsahovat počet bajtů vyžadovaných `signature` pro pole.</span><span class="sxs-lookup"><span data-stu-id="50cac-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50cac-114">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="50cac-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50cac-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="50cac-115">Requirements</span></span>  
 <span data-ttu-id="50cac-116">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50cac-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50cac-117">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="50cac-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50cac-118">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50cac-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50cac-119">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50cac-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50cac-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50cac-120">See also</span></span>

- [<span data-ttu-id="50cac-121">GetMethodProps – metoda</span><span class="sxs-lookup"><span data-stu-id="50cac-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)
- [<span data-ttu-id="50cac-122">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50cac-122">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="50cac-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="50cac-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
