---
title: ICorDebugNativeFrame::GetLocalRegisterValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterValue
helpviewer_keywords:
- GetLocalRegisterValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalRegisterValue method [.NET Framework debugging]
ms.assetid: 5ccb74f3-f891-430c-b70a-e370624edde2
topic_type:
- apiref
ms.openlocfilehash: 97d79f70097bef7768316907887cea2c38dd81e1
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212825"
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a><span data-ttu-id="bcfeb-102">ICorDebugNativeFrame::GetLocalRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="bcfeb-102">ICorDebugNativeFrame::GetLocalRegisterValue Method</span></span>
<span data-ttu-id="bcfeb-103">Získá hodnotu argumentu nebo místní proměnné, která je uložena v zadaném registru pro tento nativní rámec.</span><span class="sxs-lookup"><span data-stu-id="bcfeb-103">Gets the value of an argument or local variable that is stored in the specified register for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcfeb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcfeb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcfeb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bcfeb-105">Parameters</span></span>  
 `reg`  
 <span data-ttu-id="bcfeb-106">pro Hodnota výčtu "CorDebugRegister –", která určuje registr obsahující hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bcfeb-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="bcfeb-107">pro Celé číslo, které určuje velikost binárního podpisu metadat, na který odkazuje `pvSigBlob` parametr.</span><span class="sxs-lookup"><span data-stu-id="bcfeb-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="bcfeb-108">pro `PCCOR_SIGNATURE`Hodnota, která odkazuje na binární signaturu metadat typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bcfeb-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="bcfeb-109">mimo Ukazatel na adresu objektu "ICorDebugValue" představující načtenou hodnotu, která je uložena v zadaném registru.</span><span class="sxs-lookup"><span data-stu-id="bcfeb-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcfeb-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bcfeb-110">Remarks</span></span>  
 <span data-ttu-id="bcfeb-111">`GetLocalRegisterValue`Metodu lze použít buď v nativním rámci, nebo v rámci zkompilovaného snímku JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="bcfeb-111">The `GetLocalRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcfeb-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bcfeb-112">Requirements</span></span>  
 <span data-ttu-id="bcfeb-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcfeb-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcfeb-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bcfeb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bcfeb-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bcfeb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcfeb-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcfeb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcfeb-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="bcfeb-117">See also</span></span>
