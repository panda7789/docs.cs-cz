---
title: ICorDebugNativeFrame::GetLocalMemoryValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryValue
helpviewer_keywords:
- GetLocalMemoryValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalMemoryValue method [.NET Framework debugging]
ms.assetid: b600b3a2-9908-42d8-8093-ab6f39e9a2c9
topic_type:
- apiref
ms.openlocfilehash: 4c4bfe6a797fc1476ff53a8f2db4f80debc41f6b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212435"
---
# <a name="icordebugnativeframegetlocalmemoryvalue-method"></a><span data-ttu-id="a4dbf-102">ICorDebugNativeFrame::GetLocalMemoryValue – metoda</span><span class="sxs-lookup"><span data-stu-id="a4dbf-102">ICorDebugNativeFrame::GetLocalMemoryValue Method</span></span>
<span data-ttu-id="a4dbf-103">Získá hodnotu argumentu nebo místní proměnné, která je uložena v zadaném umístění v paměti pro tento nativní rámec.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-103">Gets the value of an argument or local variable that is stored in the specified memory location for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4dbf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4dbf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalMemoryValue (  
    [in]  CORDB_ADDRESS      address,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4dbf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4dbf-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="a4dbf-106">pro `CORDB_ADDRESS`Hodnota, která určuje umístění paměti obsahující hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="a4dbf-107">pro Celé číslo, které určuje velikost binárního podpisu metadat, na který odkazuje `pvSigBlob` parametr.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="a4dbf-108">pro `PCCOR_SIGNATURE`Hodnota, která odkazuje na binární signaturu metadat typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a4dbf-109">mimo Ukazatel na adresu objektu "ICorDebugValue" představující načtenou hodnotu, která je uložena v zadaném umístění v paměti.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4dbf-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a4dbf-110">Requirements</span></span>  
 <span data-ttu-id="a4dbf-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4dbf-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4dbf-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a4dbf-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4dbf-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a4dbf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4dbf-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4dbf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4dbf-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4dbf-115">See also</span></span>
