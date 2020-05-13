---
title: ICorDebugNativeFrame::GetLocalMemoryRegisterValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue method [.NET Framework debugging]
- GetLocalMemoryRegisterValue method
ms.assetid: 33a19f6e-1029-4d53-af64-19591c6e58ee
topic_type:
- apiref
ms.openlocfilehash: 91f0a75f127afcff89c2b92bf3ed67466b205081
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213046"
---
# <a name="icordebugnativeframegetlocalmemoryregistervalue-method"></a><span data-ttu-id="92c23-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="92c23-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue Method</span></span>
<span data-ttu-id="92c23-103">Získá hodnotu argumentu nebo místní proměnné, z nichž jsou v zadaném registru a umístění paměti pro tento nativní rámec uloženy malá slova a velká slova v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="92c23-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the specified register and memory location, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92c23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92c23-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalMemoryRegisterValue (  
    [in] CORDB_ADDRESS      highWordAddress,  
    [in] CorDebugRegister   lowWordRegister,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92c23-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92c23-105">Parameters</span></span>  
 `highWordAddress`  
 <span data-ttu-id="92c23-106">pro `CORDB_ADDRESS`Hodnota, která určuje umístění paměti obsahující vysoké slovo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="92c23-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the high word of the value.</span></span>  
  
 `lowWordRegister`  
 <span data-ttu-id="92c23-107">pro Hodnota výčtu "CorDebugRegister –", která určuje registr obsahující nedostatečné slovo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="92c23-107">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="92c23-108">pro Celé číslo, které určuje velikost binárního podpisu metadat, na který odkazuje `pvSigBlob` parametr.</span><span class="sxs-lookup"><span data-stu-id="92c23-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="92c23-109">pro `PCCOR_SIGNATURE`Hodnota, která odkazuje na binární signaturu metadat typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="92c23-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="92c23-110">mimo Ukazatel na adresu objektu "ICorDebugValue" představující načtenou hodnotu, která je uložena v zadaném registru a umístění v paměti.</span><span class="sxs-lookup"><span data-stu-id="92c23-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92c23-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="92c23-111">Requirements</span></span>  
 <span data-ttu-id="92c23-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92c23-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92c23-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="92c23-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92c23-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="92c23-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92c23-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92c23-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92c23-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="92c23-116">See also</span></span>
