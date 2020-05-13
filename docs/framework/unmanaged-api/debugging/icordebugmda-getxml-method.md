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
ms.openlocfilehash: 219aa27296dffa525bf3e2b836825437a8ce77b0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207660"
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="57be9-102">ICorDebugMDA::GetXML – metoda</span><span class="sxs-lookup"><span data-stu-id="57be9-102">ICorDebugMDA::GetXML Method</span></span>
<span data-ttu-id="57be9-103">Získá úplný datový proud XML přidružený k Pomocníkovi spravovaného ladění (MDA) reprezentovanému pomocí [ICorDebugMDA](icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="57be9-103">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57be9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57be9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57be9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57be9-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="57be9-106">pro Velikost `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="57be9-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="57be9-107">mimo Ukazatel na délku datového proudu XML.</span><span class="sxs-lookup"><span data-stu-id="57be9-107">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="57be9-108">mimo Pole, do kterého se má uložit datový proud XML.</span><span class="sxs-lookup"><span data-stu-id="57be9-108">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="57be9-109">Pole může být prázdné.</span><span class="sxs-lookup"><span data-stu-id="57be9-109">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57be9-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57be9-110">Remarks</span></span>  
 <span data-ttu-id="57be9-111">`GetXML`Metoda může ovlivnit výkon v závislosti na velikosti přidruženého datového proudu XML.</span><span class="sxs-lookup"><span data-stu-id="57be9-111">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57be9-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57be9-112">Requirements</span></span>  
 <span data-ttu-id="57be9-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57be9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57be9-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="57be9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57be9-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="57be9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57be9-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57be9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57be9-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="57be9-117">See also</span></span>

- [<span data-ttu-id="57be9-118">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57be9-118">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="57be9-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="57be9-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
