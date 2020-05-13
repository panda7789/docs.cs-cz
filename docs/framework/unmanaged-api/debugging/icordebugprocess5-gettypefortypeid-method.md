---
title: ICorDebugProcess5::GetTypeForTypeID – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeForTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeForTypeID
helpviewer_keywords:
- GetTypeForTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeForTypeID method [.NET Framework debugging]
ms.assetid: e0eed5a8-fa6d-4818-bd00-7babcea30325
topic_type:
- apiref
ms.openlocfilehash: ea7f7a9d4589e4f08b1b1e20b4d073bb5f822714
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212760"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="64c80-102">ICorDebugProcess5::GetTypeForTypeID – metoda</span><span class="sxs-lookup"><span data-stu-id="64c80-102">ICorDebugProcess5::GetTypeForTypeID Method</span></span>
<span data-ttu-id="64c80-103">Převede identifikátor typu na hodnotu ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="64c80-103">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64c80-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64c80-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64c80-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="64c80-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="64c80-106">pro Identifikátor typu.</span><span class="sxs-lookup"><span data-stu-id="64c80-106">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="64c80-107">mimo Ukazatel na adresu ICorDebugType objektu.</span><span class="sxs-lookup"><span data-stu-id="64c80-107">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64c80-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="64c80-108">Remarks</span></span>  
 <span data-ttu-id="64c80-109">V některých případech metody, které vracejí identifikátor typu, mohou vracet hodnotu null `COR_TYPEID` .</span><span class="sxs-lookup"><span data-stu-id="64c80-109">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="64c80-110">Pokud je tato hodnota předána jako `id` argument, `GetTypeForTypeID` metoda selže a vrátí `E_FAIL` .</span><span class="sxs-lookup"><span data-stu-id="64c80-110">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64c80-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="64c80-111">Requirements</span></span>  
 <span data-ttu-id="64c80-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64c80-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64c80-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="64c80-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64c80-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="64c80-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64c80-115">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64c80-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64c80-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="64c80-116">See also</span></span>

- [<span data-ttu-id="64c80-117">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64c80-117">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="64c80-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64c80-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
