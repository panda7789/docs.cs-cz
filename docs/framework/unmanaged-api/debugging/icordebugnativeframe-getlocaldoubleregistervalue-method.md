---
title: ICorDebugNativeFrame::GetLocalDoubleRegisterValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalDoubleRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue method [.NET Framework debugging]
- GetLocalDoubleRegisterValue method [.NET Framework debugging]
ms.assetid: 1f838215-ac8a-434f-8ce6-03021d3098d9
topic_type:
- apiref
ms.openlocfilehash: 21c4d00e4156b9db27ae4188aace19764a2be53e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213072"
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a><span data-ttu-id="4925a-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="4925a-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue Method</span></span>
<span data-ttu-id="4925a-103">Získá hodnotu argumentu nebo místní proměnné, která je uložena ve dvou zadaných registrech pro tento nativní rámec.</span><span class="sxs-lookup"><span data-stu-id="4925a-103">Gets the value of an argument or local variable that is stored in the two specified registers for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4925a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4925a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4925a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4925a-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="4925a-106">pro Hodnota výčtu "CorDebugRegister –", která určuje registr obsahující vysoké slovo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4925a-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordReg`  
 <span data-ttu-id="4925a-107">pro Hodnota `CorDebugRegister` výčtu, která určuje registr obsahující nedostatečné slovo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4925a-107">[in] A value of the `CorDebugRegister` enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="4925a-108">pro Celé číslo, které určuje velikost binárního podpisu metadat, na který odkazuje `pvSigBlob` parametr.</span><span class="sxs-lookup"><span data-stu-id="4925a-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="4925a-109">pro `PCCOR_SIGNATURE`Hodnota, která odkazuje na binární signaturu metadat typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4925a-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="4925a-110">mimo Ukazatel na adresu objektu "ICorDebugValue" představující načtenou hodnotu, která je uložena v zadaných registrech.</span><span class="sxs-lookup"><span data-stu-id="4925a-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified registers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4925a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4925a-111">Remarks</span></span>  
 <span data-ttu-id="4925a-112">`GetLocalDoubleRegisterValue`Metodu lze použít buď v nativním rámci, nebo v rámci zkompilovaného snímku JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="4925a-112">The `GetLocalDoubleRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4925a-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4925a-113">Requirements</span></span>  
 <span data-ttu-id="4925a-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4925a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4925a-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4925a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4925a-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4925a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4925a-117">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4925a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4925a-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="4925a-118">See also</span></span>
