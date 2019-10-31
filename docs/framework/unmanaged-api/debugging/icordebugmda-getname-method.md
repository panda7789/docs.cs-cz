---
title: ICorDebugMDA::GetName – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetName
helpviewer_keywords:
- ICorDebugMDA::GetName method [.NET Framework debugging]
- GetName method, ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 885bf5e8-00b7-4cd7-9d8d-e720d47918c4
topic_type:
- apiref
ms.openlocfilehash: 1b19ce5e9f795fd9ff4dd15e10256a150063a314
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128045"
---
# <a name="icordebugmdagetname-method"></a><span data-ttu-id="db6a6-102">ICorDebugMDA::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="db6a6-102">ICorDebugMDA::GetName Method</span></span>
<span data-ttu-id="db6a6-103">Získá řetězec obsahující název pomocníka spravovaného ladění (MDA) reprezentovaný [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="db6a6-103">Gets a string containing the name of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db6a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db6a6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db6a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db6a6-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="db6a6-106">pro Velikost pole `szName`.</span><span class="sxs-lookup"><span data-stu-id="db6a6-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="db6a6-107">mimo Ukazatel na délku názvu.</span><span class="sxs-lookup"><span data-stu-id="db6a6-107">[out] A pointer to the length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="db6a6-108">mimo Pole, do kterého se má uložit název</span><span class="sxs-lookup"><span data-stu-id="db6a6-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db6a6-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db6a6-109">Remarks</span></span>  
 <span data-ttu-id="db6a6-110">Názvy MDA jsou jedinečné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="db6a6-110">MDA names are unique values.</span></span> <span data-ttu-id="db6a6-111">Metoda `GetName` je pohodlný alternativní výkon pro získání datového proudu XML a extrakci názvu z datového proudu založeného na schématu.</span><span class="sxs-lookup"><span data-stu-id="db6a6-111">The `GetName` method is a convenient performance alternative to getting the XML stream and extracting the name from the stream based on the schema.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db6a6-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db6a6-112">Requirements</span></span>  
 <span data-ttu-id="db6a6-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db6a6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db6a6-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="db6a6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db6a6-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="db6a6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db6a6-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db6a6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db6a6-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db6a6-117">See also</span></span>

- [<span data-ttu-id="db6a6-118">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db6a6-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="db6a6-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="db6a6-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
