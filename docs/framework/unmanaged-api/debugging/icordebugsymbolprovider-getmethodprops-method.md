---
title: "ICorDebugSymbolProvider::GetMethodProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 58406f3f47e5d6eabd55420dc57148dc7f264726
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="b2ed4-102">ICorDebugSymbolProvider::GetMethodProps – metoda</span><span class="sxs-lookup"><span data-stu-id="b2ed4-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="b2ed4-103">Zadaná relativní virtuální adresy (RVA) v dané metody vrací informace o vlastnosti metoda, například metadata token a informace o jeho obecné parametry metody.</span><span class="sxs-lookup"><span data-stu-id="b2ed4-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2ed4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2ed4-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="b2ed4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2ed4-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="b2ed4-106">[v] Relativní virtuální adresu v metodě o tom, které informace se mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="b2ed4-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="b2ed4-107">[out] Ukazatel na metodu na token metadat.</span><span class="sxs-lookup"><span data-stu-id="b2ed4-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="b2ed4-108">[out] Ukazatel na počet obecné parametry přidružený k této metodě.</span><span class="sxs-lookup"><span data-stu-id="b2ed4-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="b2ed4-109">[v] Velikost `signature` pole.</span><span class="sxs-lookup"><span data-stu-id="b2ed4-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="b2ed4-110">Najdete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="b2ed4-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="b2ed4-111">[out] Ukazatel na velikost vrácený `signature` pole.</span><span class="sxs-lookup"><span data-stu-id="b2ed4-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="b2ed4-112">[out] Vyrovnávací paměť, která obsahuje typ typespec signatur všechny obecné parametry.</span><span class="sxs-lookup"><span data-stu-id="b2ed4-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2ed4-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b2ed4-113">Remarks</span></span>  
 <span data-ttu-id="b2ed4-114">Chcete-li získat požadovaná velikost metoda `signature` pole, nastavte `cbSignature` argument na hodnotu 0 a `signature` k **hodnotu null**.</span><span class="sxs-lookup"><span data-stu-id="b2ed4-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="b2ed4-115">Po návratu metody `pcbSignature` bude obsahovat počet bajtů požadovaných pro `signature` pole.</span><span class="sxs-lookup"><span data-stu-id="b2ed4-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2ed4-116">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="b2ed4-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2ed4-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b2ed4-117">Requirements</span></span>  
 <span data-ttu-id="b2ed4-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2ed4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2ed4-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2ed4-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2ed4-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2ed4-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2ed4-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2ed4-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2ed4-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2ed4-122">See Also</span></span>  
 [<span data-ttu-id="b2ed4-123">GetTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="b2ed4-123">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)  
 [<span data-ttu-id="b2ed4-124">ICorDebugSymbolProvider rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2ed4-124">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="b2ed4-125">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2ed4-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
