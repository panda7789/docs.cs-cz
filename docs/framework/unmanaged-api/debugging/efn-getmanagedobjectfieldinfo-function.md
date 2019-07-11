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
ms.openlocfilehash: c1de0b3b05d38c1fec38b9436c653973dfaa4136
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739010"
---
# <a name="efngetmanagedobjectfieldinfo-function"></a><span data-ttu-id="f7183-102">\_EFN\_GetManagedObjectFieldInfo Function</span><span class="sxs-lookup"><span data-stu-id="f7183-102">\_EFN\_GetManagedObjectFieldInfo Function</span></span>
<span data-ttu-id="f7183-103">Získá posun od začátku objekt pole a hodnota pole pomocí ukazatele zadaného objektu a název pole.</span><span class="sxs-lookup"><span data-stu-id="f7183-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7183-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7183-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7183-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7183-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="f7183-106">[in] Ukazatel na klientovi ladění.</span><span class="sxs-lookup"><span data-stu-id="f7183-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="f7183-107">[in] Ukazatel spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="f7183-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="f7183-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="f7183-108">szFieldName</span></span>  
 <span data-ttu-id="f7183-109">[in] Spravovaný objekt ukazatel na název pole.</span><span class="sxs-lookup"><span data-stu-id="f7183-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="f7183-110">[out] Hodnota pole.</span><span class="sxs-lookup"><span data-stu-id="f7183-110">[out] The field value.</span></span> <span data-ttu-id="f7183-111">Tento parametr může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="f7183-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="f7183-112">[out] Posun od `objAddr` do příslušného pole.</span><span class="sxs-lookup"><span data-stu-id="f7183-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="f7183-113">Tento parametr může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="f7183-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7183-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f7183-114">Remarks</span></span>  
 <span data-ttu-id="f7183-115">Pokud posun je 0, je zapsán bez posunutí.</span><span class="sxs-lookup"><span data-stu-id="f7183-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="f7183-116">Pokud neexistuje žádný spravovaný kód ve vlákně aktuálně v kontextu, funkce vrátí HRESULT SOS_E_NOMANAGEDCODE s hodnotou zařízení 0xa0 a 0x1000 kód chyby.</span><span class="sxs-lookup"><span data-stu-id="f7183-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7183-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7183-117">Requirements</span></span>  
 <span data-ttu-id="f7183-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7183-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7183-119">**Záhlaví:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="f7183-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="f7183-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7183-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7183-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7183-121">See also</span></span>

- [<span data-ttu-id="f7183-122">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="f7183-122">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
