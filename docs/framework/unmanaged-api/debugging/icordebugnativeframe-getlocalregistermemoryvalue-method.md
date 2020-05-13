---
title: ICorDebugNativeFrame::GetLocalRegisterMemoryValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue method [.NET Framework debugging]
- GetLocalRegisterMemoryValue method [.NET Framework debugging]
ms.assetid: d350f69d-9aff-4f5a-8301-daea22dee2da
topic_type:
- apiref
ms.openlocfilehash: f16150ad7d9ecec4b4aceee5c9266e9a7859f1cb
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213293"
---
# <a name="icordebugnativeframegetlocalregistermemoryvalue-method"></a><span data-ttu-id="b84ff-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue – metoda</span><span class="sxs-lookup"><span data-stu-id="b84ff-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue Method</span></span>
<span data-ttu-id="b84ff-103">Získá hodnotu argumentu nebo místní proměnné, z nichž je pro tento nativní rámec uloženo méně slov a vysoké slovo v umístění paměti a určeném registru.</span><span class="sxs-lookup"><span data-stu-id="b84ff-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the memory location and specified register, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b84ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b84ff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalRegisterMemoryValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CORDB_ADDRESS      lowWordAddress,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b84ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b84ff-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="b84ff-106">pro Hodnota výčtu "CorDebugRegister –", která určuje registr obsahující vysoké slovo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b84ff-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordAddress`  
 <span data-ttu-id="b84ff-107">pro `CORDB_ADDRESS`Hodnota, která určuje umístění paměti obsahující nedostatečné slovo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b84ff-107">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="b84ff-108">pro Celé číslo, které určuje velikost binárního podpisu metadat, na který odkazuje `pvSigBlob` parametr.</span><span class="sxs-lookup"><span data-stu-id="b84ff-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="b84ff-109">pro `PCCOR_SIGNATURE`Hodnota, která odkazuje na binární signaturu metadat typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b84ff-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="b84ff-110">mimo Ukazatel na adresu objektu "ICorDebugValue" představující načtenou hodnotu, která je uložena v zadaném registru a umístění v paměti.</span><span class="sxs-lookup"><span data-stu-id="b84ff-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b84ff-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b84ff-111">Requirements</span></span>  
 <span data-ttu-id="b84ff-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b84ff-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b84ff-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b84ff-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b84ff-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b84ff-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b84ff-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b84ff-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b84ff-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b84ff-116">See also</span></span>
