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
ms.openlocfilehash: 522ac2fd448abaaba48d4d5c20551e8029b35fd4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793234"
---
# <a name="icordebugmdagetname-method"></a><span data-ttu-id="36c68-102">ICorDebugMDA::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="36c68-102">ICorDebugMDA::GetName Method</span></span>
<span data-ttu-id="36c68-103">Získá řetězec obsahující název pomocníka spravovaného ladění (MDA) reprezentovaný [ICorDebugMDA](icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="36c68-103">Gets a string containing the name of the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36c68-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36c68-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36c68-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36c68-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="36c68-106">pro Velikost pole `szName`.</span><span class="sxs-lookup"><span data-stu-id="36c68-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="36c68-107">mimo Ukazatel na délku názvu.</span><span class="sxs-lookup"><span data-stu-id="36c68-107">[out] A pointer to the length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="36c68-108">mimo Pole, do kterého se má uložit název</span><span class="sxs-lookup"><span data-stu-id="36c68-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36c68-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36c68-109">Remarks</span></span>  
 <span data-ttu-id="36c68-110">Názvy MDA jsou jedinečné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="36c68-110">MDA names are unique values.</span></span> <span data-ttu-id="36c68-111">Metoda `GetName` je pohodlný alternativní výkon pro získání datového proudu XML a extrakci názvu z datového proudu založeného na schématu.</span><span class="sxs-lookup"><span data-stu-id="36c68-111">The `GetName` method is a convenient performance alternative to getting the XML stream and extracting the name from the stream based on the schema.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36c68-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36c68-112">Requirements</span></span>  
 <span data-ttu-id="36c68-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36c68-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36c68-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="36c68-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36c68-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="36c68-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36c68-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36c68-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36c68-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="36c68-117">See also</span></span>

- [<span data-ttu-id="36c68-118">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="36c68-118">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="36c68-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="36c68-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
