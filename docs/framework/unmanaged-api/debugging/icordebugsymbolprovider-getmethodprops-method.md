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
ms.workload: dotnet
ms.openlocfilehash: cf92727139dc912107484b1e13944c679c944726
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="12b90-102">ICorDebugSymbolProvider::GetMethodProps – metoda</span><span class="sxs-lookup"><span data-stu-id="12b90-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="12b90-103">Zadaná relativní virtuální adresy (RVA) v dané metody vrací informace o vlastnosti metoda, například metadata token a informace o jeho obecné parametry metody.</span><span class="sxs-lookup"><span data-stu-id="12b90-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12b90-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12b90-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="12b90-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="12b90-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="12b90-106">[v] Relativní virtuální adresu v metodě o tom, které informace se mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="12b90-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="12b90-107">[out] Ukazatel na metodu na token metadat.</span><span class="sxs-lookup"><span data-stu-id="12b90-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="12b90-108">[out] Ukazatel na počet obecné parametry přidružený k této metodě.</span><span class="sxs-lookup"><span data-stu-id="12b90-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="12b90-109">[v] Velikost `signature` pole.</span><span class="sxs-lookup"><span data-stu-id="12b90-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="12b90-110">Najdete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="12b90-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="12b90-111">[out] Ukazatel na velikost vrácený `signature` pole.</span><span class="sxs-lookup"><span data-stu-id="12b90-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="12b90-112">[out] Vyrovnávací paměť, která obsahuje typ typespec signatur všechny obecné parametry.</span><span class="sxs-lookup"><span data-stu-id="12b90-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12b90-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12b90-113">Remarks</span></span>  
 <span data-ttu-id="12b90-114">Chcete-li získat požadovaná velikost metoda `signature` pole, nastavte `cbSignature` argument na hodnotu 0 a `signature` k **hodnotu null**.</span><span class="sxs-lookup"><span data-stu-id="12b90-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="12b90-115">Po návratu metody `pcbSignature` bude obsahovat počet bajtů požadovaných pro `signature` pole.</span><span class="sxs-lookup"><span data-stu-id="12b90-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="12b90-116">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="12b90-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12b90-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12b90-117">Requirements</span></span>  
 <span data-ttu-id="12b90-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12b90-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12b90-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12b90-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12b90-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12b90-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12b90-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12b90-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12b90-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="12b90-122">See Also</span></span>  
 [<span data-ttu-id="12b90-123">GetTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="12b90-123">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)  
 [<span data-ttu-id="12b90-124">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12b90-124">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="12b90-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="12b90-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
