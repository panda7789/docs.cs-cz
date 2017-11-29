---
title: "ICorDebugMDA::GetName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMDA.GetName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMDA::GetName
helpviewer_keywords:
- ICorDebugMDA::GetName method [.NET Framework debugging]
- GetName method, ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 885bf5e8-00b7-4cd7-9d8d-e720d47918c4
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 23c750c0eafff9364b9c75bf1b9fe9e478f09867
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmdagetname-method"></a><span data-ttu-id="762cb-102">ICorDebugMDA::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="762cb-102">ICorDebugMDA::GetName Method</span></span>
<span data-ttu-id="762cb-103">Získá řetězec obsahující název Pomocník spravovaného ladění (MDA) reprezentována [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="762cb-103">Gets a string containing the name of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="762cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="762cb-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="762cb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="762cb-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="762cb-106">[v] Velikost `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="762cb-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="762cb-107">[out] Ukazatel na délku názvu.</span><span class="sxs-lookup"><span data-stu-id="762cb-107">[out] A pointer to the length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="762cb-108">[out] Pole, do které chcete uložit název.</span><span class="sxs-lookup"><span data-stu-id="762cb-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="762cb-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="762cb-109">Remarks</span></span>  
 <span data-ttu-id="762cb-110">MDA názvy jsou jedinečné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="762cb-110">MDA names are unique values.</span></span> <span data-ttu-id="762cb-111">`GetName` Metoda je vhodné výkonu alternativou k získávání datový proud XML a extrahování název z datového proudu na základě schématu.</span><span class="sxs-lookup"><span data-stu-id="762cb-111">The `GetName` method is a convenient performance alternative to getting the XML stream and extracting the name from the stream based on the schema.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="762cb-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="762cb-112">Requirements</span></span>  
 <span data-ttu-id="762cb-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="762cb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="762cb-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="762cb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="762cb-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="762cb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="762cb-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="762cb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="762cb-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="762cb-117">See Also</span></span>  
 [<span data-ttu-id="762cb-118">ICorDebugMDA – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="762cb-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [<span data-ttu-id="762cb-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="762cb-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
