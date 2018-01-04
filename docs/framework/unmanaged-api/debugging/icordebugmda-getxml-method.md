---
title: "ICorDebugMDA::GetXML – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMDA.GetXML
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 387c9bf53dfbe146ccc1526404a1aed7386b2519
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="588fb-102">ICorDebugMDA::GetXML – metoda</span><span class="sxs-lookup"><span data-stu-id="588fb-102">ICorDebugMDA::GetXML Method</span></span>
<span data-ttu-id="588fb-103">Získá úplný datový proud XML přidružené Pomocník spravovaného ladění (MDA) reprezentována [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="588fb-103">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="588fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="588fb-104">Syntax</span></span>  
  
```  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="588fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="588fb-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="588fb-106">[v] Velikost `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="588fb-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="588fb-107">[out] Ukazatel na délku datového proudu XML.</span><span class="sxs-lookup"><span data-stu-id="588fb-107">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="588fb-108">[out] Pole, do které chcete uložit datový proud XML.</span><span class="sxs-lookup"><span data-stu-id="588fb-108">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="588fb-109">Pole může být prázdná.</span><span class="sxs-lookup"><span data-stu-id="588fb-109">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="588fb-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="588fb-110">Remarks</span></span>  
 <span data-ttu-id="588fb-111">`GetXML` Metoda může potenciálně ovlivnit výkon, v závislosti na velikosti související datový proud XML.</span><span class="sxs-lookup"><span data-stu-id="588fb-111">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="588fb-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="588fb-112">Requirements</span></span>  
 <span data-ttu-id="588fb-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="588fb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="588fb-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="588fb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="588fb-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="588fb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="588fb-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="588fb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="588fb-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="588fb-117">See Also</span></span>  
 [<span data-ttu-id="588fb-118">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="588fb-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [<span data-ttu-id="588fb-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="588fb-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
