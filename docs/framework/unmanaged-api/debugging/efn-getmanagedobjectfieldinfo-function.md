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
ms.openlocfilehash: 182424632e4f81dfdf86e87dc6bb2c75c2780fce
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793760"
---
# <a name="_efn_getmanagedobjectfieldinfo-function"></a><span data-ttu-id="e3ba3-102">\_EFN\_GetManagedObjectFieldInfo Function</span><span class="sxs-lookup"><span data-stu-id="e3ba3-102">\_EFN\_GetManagedObjectFieldInfo Function</span></span>
<span data-ttu-id="e3ba3-103">Získá posun od začátku objektu k poli a hodnotu pole pomocí zadaného ukazatele objektu a názvu pole.</span><span class="sxs-lookup"><span data-stu-id="e3ba3-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3ba3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3ba3-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3ba3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3ba3-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="e3ba3-106">pro Ukazatel na ladicího klienta.</span><span class="sxs-lookup"><span data-stu-id="e3ba3-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="e3ba3-107">pro Ukazatel spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="e3ba3-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="e3ba3-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="e3ba3-108">szFieldName</span></span>  
 <span data-ttu-id="e3ba3-109">pro Ukazatel spravovaného objektu na název pole.</span><span class="sxs-lookup"><span data-stu-id="e3ba3-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="e3ba3-110">mimo Hodnota pole</span><span class="sxs-lookup"><span data-stu-id="e3ba3-110">[out] The field value.</span></span> <span data-ttu-id="e3ba3-111">Tento parametr může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="e3ba3-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="e3ba3-112">mimo Posun od `objAddr` k poli.</span><span class="sxs-lookup"><span data-stu-id="e3ba3-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="e3ba3-113">Tento parametr může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="e3ba3-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3ba3-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e3ba3-114">Remarks</span></span>  
 <span data-ttu-id="e3ba3-115">Pokud je posun 0, není zapsán žádný posun.</span><span class="sxs-lookup"><span data-stu-id="e3ba3-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="e3ba3-116">Pokud ve vlákně, který je aktuálně v kontextu, není žádný spravovaný kód, funkce vrátí hodnotu HRESULT SOS_E_NOMANAGEDCODE s hodnotou zařízení 0xa0 a kódem chyby 0x1000.</span><span class="sxs-lookup"><span data-stu-id="e3ba3-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3ba3-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e3ba3-117">Requirements</span></span>  
 <span data-ttu-id="e3ba3-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3ba3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3ba3-119">**Hlavička:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="e3ba3-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="e3ba3-120">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3ba3-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3ba3-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3ba3-121">See also</span></span>

- [<span data-ttu-id="e3ba3-122">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="e3ba3-122">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
