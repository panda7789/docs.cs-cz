---
title: ICorDebugValue::GetSize – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type:
- apiref
ms.openlocfilehash: 9ff7128f55236ae4d0c3a9067a279c496cfb6798
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396752"
---
# <a name="icordebugvaluegetsize-method"></a><span data-ttu-id="20b62-102">ICorDebugValue::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="20b62-102">ICorDebugValue::GetSize Method</span></span>
<span data-ttu-id="20b62-103">Získá velikost objektu "ICorDebugValue" v bajtech.</span><span class="sxs-lookup"><span data-stu-id="20b62-103">Gets the size, in bytes, of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20b62-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20b62-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20b62-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="20b62-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="20b62-106">mimo Velikost objektu Value (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="20b62-106">[out] The size, in bytes, of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20b62-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20b62-107">Remarks</span></span>  
 <span data-ttu-id="20b62-108">Pokud je typ hodnoty odkazový typ, tato metoda vrátí velikost ukazatele místo velikosti objektu.</span><span class="sxs-lookup"><span data-stu-id="20b62-108">If the value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="20b62-109">`ICorDebugValue::GetSize`Metoda vrací `COR_E_OVERFLOW` objekty, které jsou větší než 4 GB na 64 bitů.</span><span class="sxs-lookup"><span data-stu-id="20b62-109">The `ICorDebugValue::GetSize` method returns `COR_E_OVERFLOW` for objects that are larger than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="20b62-110">Použijte raději metodu [ICorDebugValue3 –:: GetSize64 –](icordebugvalue3-getsize64-method.md) pro objekty, které jsou větší než 4 GB.</span><span class="sxs-lookup"><span data-stu-id="20b62-110">Use the [ICorDebugValue3::GetSize64](icordebugvalue3-getsize64-method.md) method instead for objects that are larger than 4 GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20b62-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20b62-111">Requirements</span></span>  
 <span data-ttu-id="20b62-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20b62-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20b62-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="20b62-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20b62-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="20b62-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20b62-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20b62-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20b62-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="20b62-116">See also</span></span>

- [<span data-ttu-id="20b62-117">GetSize64 – metoda</span><span class="sxs-lookup"><span data-stu-id="20b62-117">GetSize64 Method</span></span>](icordebugvalue3-getsize64-method.md)
