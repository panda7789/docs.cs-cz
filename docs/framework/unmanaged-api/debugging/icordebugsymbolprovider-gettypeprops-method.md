---
title: ICorDebugSymbolProvider::GetTypeProps – metoda
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5f9867dbdc244ed22948dbe9a07a7ea06292d6a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079081"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="ad981-102">ICorDebugSymbolProvider::GetTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="ad981-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>
<span data-ttu-id="ad981-103">Vrátí informace o typu vlastnosti, jako je počet podpis jeho obecné parametry-li zadána relativní virtuální adresu (RVA) v tabulku vtable.</span><span class="sxs-lookup"><span data-stu-id="ad981-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad981-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad981-104">Syntax</span></span>  
  
```  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad981-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad981-105">Parameters</span></span>  
 `tableRva`  
 <span data-ttu-id="ad981-106">[in] Relativní virtuální adresu (RVA) v tabulku vtable.</span><span class="sxs-lookup"><span data-stu-id="ad981-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="ad981-107">[in] Velikost `signature` pole.</span><span class="sxs-lookup"><span data-stu-id="ad981-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="ad981-108">V části poznámky.</span><span class="sxs-lookup"><span data-stu-id="ad981-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="ad981-109">[out] [out] Ukazatel na velikost vráceného `signature` pole.</span><span class="sxs-lookup"><span data-stu-id="ad981-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="ad981-110">[out] Vyrovnávací paměti, který obsahuje token typespec podpisy všechny obecné parametry.</span><span class="sxs-lookup"><span data-stu-id="ad981-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad981-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad981-111">Remarks</span></span>  
 <span data-ttu-id="ad981-112">Chcete-li získat požadovaná velikost tohoto typu `signature` pole, nastavte `cbSignature` argumentu na hodnotu 0 a `signature` k **null**.</span><span class="sxs-lookup"><span data-stu-id="ad981-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="ad981-113">Po návratu metody `pcbSignature` bude obsahovat počet bajtů potřebných pro `signature` pole.</span><span class="sxs-lookup"><span data-stu-id="ad981-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad981-114">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ad981-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad981-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad981-115">Requirements</span></span>  
 <span data-ttu-id="ad981-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad981-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad981-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad981-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad981-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad981-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ad981-119">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ad981-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ad981-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad981-120">See also</span></span>

- [<span data-ttu-id="ad981-121">GetMethodProps – metoda</span><span class="sxs-lookup"><span data-stu-id="ad981-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)
- [<span data-ttu-id="ad981-122">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad981-122">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="ad981-123">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad981-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
