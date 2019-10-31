---
title: ICorDebugMDA::GetXML – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetXML
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type:
- apiref
ms.openlocfilehash: f80bdffbf5c0ba39980bd27c6e89a368547340c0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129812"
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="65952-102">ICorDebugMDA::GetXML – metoda</span><span class="sxs-lookup"><span data-stu-id="65952-102">ICorDebugMDA::GetXML Method</span></span>
<span data-ttu-id="65952-103">Získá úplný datový proud XML přidružený k Pomocníkovi spravovaného ladění (MDA) reprezentovanému pomocí [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="65952-103">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65952-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65952-104">Syntax</span></span>  
  
```cpp  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65952-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65952-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="65952-106">pro Velikost pole `szName`.</span><span class="sxs-lookup"><span data-stu-id="65952-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="65952-107">mimo Ukazatel na délku datového proudu XML.</span><span class="sxs-lookup"><span data-stu-id="65952-107">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="65952-108">mimo Pole, do kterého se má uložit datový proud XML.</span><span class="sxs-lookup"><span data-stu-id="65952-108">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="65952-109">Pole může být prázdné.</span><span class="sxs-lookup"><span data-stu-id="65952-109">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65952-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65952-110">Remarks</span></span>  
 <span data-ttu-id="65952-111">Metoda `GetXML` může ovlivnit výkon v závislosti na velikosti přidruženého datového proudu XML.</span><span class="sxs-lookup"><span data-stu-id="65952-111">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65952-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65952-112">Requirements</span></span>  
 <span data-ttu-id="65952-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65952-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65952-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="65952-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65952-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="65952-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65952-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65952-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65952-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65952-117">See also</span></span>

- [<span data-ttu-id="65952-118">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65952-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="65952-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="65952-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
