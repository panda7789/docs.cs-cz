---
title: _EFN_GetManagedObjectFieldInfo – funkce
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectFieldInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectFieldInfo
helpviewer_keywords:
- _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e7d031d4a4f4e67134f4b88f3e3ff47316ce3b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183141"
---
# <a name="efngetmanagedobjectfieldinfo-function"></a><span data-ttu-id="af66f-102">_EFN_GetManagedObjectFieldInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="af66f-102">_EFN_GetManagedObjectFieldInfo Function</span></span>
<span data-ttu-id="af66f-103">Získá posun od začátku objekt pole a hodnota pole pomocí ukazatele zadaného objektu a název pole.</span><span class="sxs-lookup"><span data-stu-id="af66f-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af66f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af66f-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af66f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="af66f-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="af66f-106">[in] Ukazatel na klientovi ladění.</span><span class="sxs-lookup"><span data-stu-id="af66f-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="af66f-107">[in] Ukazatel spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="af66f-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="af66f-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="af66f-108">szFieldName</span></span>  
 <span data-ttu-id="af66f-109">[in] Spravovaný objekt ukazatel na název pole.</span><span class="sxs-lookup"><span data-stu-id="af66f-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="af66f-110">[out] Hodnota pole.</span><span class="sxs-lookup"><span data-stu-id="af66f-110">[out] The field value.</span></span> <span data-ttu-id="af66f-111">Tento parametr může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="af66f-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="af66f-112">[out] Posun od `objAddr` do příslušného pole.</span><span class="sxs-lookup"><span data-stu-id="af66f-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="af66f-113">Tento parametr může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="af66f-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af66f-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af66f-114">Remarks</span></span>  
 <span data-ttu-id="af66f-115">Pokud posun je 0, je zapsán bez posunutí.</span><span class="sxs-lookup"><span data-stu-id="af66f-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="af66f-116">Pokud neexistuje žádný spravovaný kód ve vlákně aktuálně v kontextu, funkce vrátí HRESULT SOS_E_NOMANAGEDCODE s hodnotou zařízení 0xa0 a 0x1000 kód chyby.</span><span class="sxs-lookup"><span data-stu-id="af66f-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af66f-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="af66f-117">Requirements</span></span>  
 <span data-ttu-id="af66f-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af66f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af66f-119">**Záhlaví:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="af66f-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 **<span data-ttu-id="af66f-120">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="af66f-120">.NET Framework Version:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="af66f-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af66f-121">See also</span></span>

- [<span data-ttu-id="af66f-122">Globální statické funkce ladění</span><span class="sxs-lookup"><span data-stu-id="af66f-122">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
