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
ms.openlocfilehash: d44d7c23f88f5ea93f608d06b69f69b2c3637b5e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096849"
---
# <a name="icordebugnativeframegetlocalregistermemoryvalue-method"></a><span data-ttu-id="fabf1-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue – metoda</span><span class="sxs-lookup"><span data-stu-id="fabf1-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue Method</span></span>
<span data-ttu-id="fabf1-103">Získá hodnotu argumentu nebo místní proměnné, z nichž je pro tento nativní rámec uloženo méně slov a vysoké slovo v umístění paměti a určeném registru.</span><span class="sxs-lookup"><span data-stu-id="fabf1-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the memory location and specified register, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fabf1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fabf1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalRegisterMemoryValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CORDB_ADDRESS      lowWordAddress,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fabf1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fabf1-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="fabf1-106">pro Hodnota výčtu "CorDebugRegister –", která určuje registr obsahující vysoké slovo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="fabf1-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordAddress`  
 <span data-ttu-id="fabf1-107">pro Hodnota `CORDB_ADDRESS`, která určuje umístění paměti obsahující nedostatečné slovo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="fabf1-107">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="fabf1-108">pro Celé číslo, které určuje velikost binárního podpisu metadat, na které odkazuje parametr `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="fabf1-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="fabf1-109">pro Hodnota `PCCOR_SIGNATURE`, která odkazuje na binární signaturu metadat typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="fabf1-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="fabf1-110">mimo Ukazatel na adresu objektu "ICorDebugValue" představující načtenou hodnotu, která je uložena v zadaném registru a umístění v paměti.</span><span class="sxs-lookup"><span data-stu-id="fabf1-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fabf1-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fabf1-111">Requirements</span></span>  
 <span data-ttu-id="fabf1-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fabf1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fabf1-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fabf1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fabf1-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fabf1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fabf1-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fabf1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fabf1-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fabf1-116">See also</span></span>
