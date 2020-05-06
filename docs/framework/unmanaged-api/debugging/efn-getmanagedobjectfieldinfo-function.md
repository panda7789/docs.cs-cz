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
ms.openlocfilehash: 42f7020212dd2db793b7c7d20a15c129157e7261
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860763"
---
# <a name="_efn_getmanagedobjectfieldinfo-function"></a><span data-ttu-id="03f10-102">\_EFN\_– funkce GetManagedObjectFieldInfo</span><span class="sxs-lookup"><span data-stu-id="03f10-102">\_EFN\_GetManagedObjectFieldInfo Function</span></span>
<span data-ttu-id="03f10-103">Získá posun od začátku objektu k poli a hodnotu pole pomocí zadaného ukazatele objektu a názvu pole.</span><span class="sxs-lookup"><span data-stu-id="03f10-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03f10-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03f10-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03f10-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03f10-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="03f10-106">pro Ukazatel na ladicího klienta.</span><span class="sxs-lookup"><span data-stu-id="03f10-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="03f10-107">pro Ukazatel spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="03f10-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="03f10-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="03f10-108">szFieldName</span></span>  
 <span data-ttu-id="03f10-109">pro Ukazatel spravovaného objektu na název pole.</span><span class="sxs-lookup"><span data-stu-id="03f10-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="03f10-110">mimo Hodnota pole</span><span class="sxs-lookup"><span data-stu-id="03f10-110">[out] The field value.</span></span> <span data-ttu-id="03f10-111">Tento parametr může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="03f10-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="03f10-112">mimo Posun od `objAddr` k poli.</span><span class="sxs-lookup"><span data-stu-id="03f10-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="03f10-113">Tento parametr může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="03f10-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03f10-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03f10-114">Remarks</span></span>  
 <span data-ttu-id="03f10-115">Pokud je posun 0, není zapsán žádný posun.</span><span class="sxs-lookup"><span data-stu-id="03f10-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="03f10-116">Pokud ve vlákně, který je aktuálně v kontextu, není žádný spravovaný kód, funkce vrátí hodnotu HRESULT SOS_E_NOMANAGEDCODE s hodnotou zařízení 0xa0 a kódem chyby 0x1000.</span><span class="sxs-lookup"><span data-stu-id="03f10-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03f10-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03f10-117">Requirements</span></span>  
 <span data-ttu-id="03f10-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03f10-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03f10-119">**Hlavička:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="03f10-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="03f10-120">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03f10-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03f10-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="03f10-121">See also</span></span>

- [<span data-ttu-id="03f10-122">Globální statické funkce ladění</span><span class="sxs-lookup"><span data-stu-id="03f10-122">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
