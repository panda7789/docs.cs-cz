---
title: ICorDebugSymbolProvider::GetMethodProps – metoda
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9dacfd6538dbf42a757a0e3534978238421644ae
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490434"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="6fd1d-102">ICorDebugSymbolProvider::GetMethodProps – metoda</span><span class="sxs-lookup"><span data-stu-id="6fd1d-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="6fd1d-103">Vrátí informace o vlastnostech metody, jako je například token metadat a informace o obecných parametrů, metody-li zadána relativní virtuální adresu (RVA) v této metodě.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fd1d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fd1d-104">Syntax</span></span>  
  
```  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fd1d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6fd1d-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="6fd1d-106">[in] Relativní virtuální adresu v metodě o tom, které má být načtena informace.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="6fd1d-107">[out] Ukazatel na metody token metadat.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="6fd1d-108">[out] Ukazatel na počet obecných parametrů, které jsou přidružené k této metodě.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="6fd1d-109">[in] Velikost `signature` pole.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="6fd1d-110">V části poznámky.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="6fd1d-111">[out] Ukazatel na velikost vráceného `signature` pole.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="6fd1d-112">[out] Vyrovnávací paměti, který obsahuje token typespec podpisy všechny obecné parametry.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fd1d-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6fd1d-113">Remarks</span></span>  
 <span data-ttu-id="6fd1d-114">Chcete-li získat požadovaná velikost metody `signature` pole, nastavte `cbSignature` argumentu na hodnotu 0 a `signature` k **null**.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="6fd1d-115">Po návratu metody `pcbSignature` bude obsahovat počet bajtů potřebných pro `signature` pole.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6fd1d-116">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fd1d-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6fd1d-117">Requirements</span></span>  
 <span data-ttu-id="6fd1d-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fd1d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fd1d-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6fd1d-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6fd1d-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6fd1d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fd1d-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fd1d-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fd1d-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6fd1d-122">See also</span></span>
- [<span data-ttu-id="6fd1d-123">GetTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="6fd1d-123">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="6fd1d-124">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6fd1d-124">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="6fd1d-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6fd1d-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
