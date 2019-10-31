---
title: _EFN_GetManagedObjectName – funkce
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectName
helpviewer_keywords:
- _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type:
- apiref
ms.openlocfilehash: c7333f8f7b95655ac821e9a2977d5db3794486a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123007"
---
# <a name="_efn_getmanagedobjectname-function"></a><span data-ttu-id="fd995-102">\_EFN\_funkce GetManagedObjectName</span><span class="sxs-lookup"><span data-stu-id="fd995-102">\_EFN\_GetManagedObjectName Function</span></span>
<span data-ttu-id="fd995-103">Získá název typu pomocí zadaného ukazatele spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="fd995-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd995-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd995-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd995-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fd995-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="fd995-106">pro Ukazatel na ladicího klienta.</span><span class="sxs-lookup"><span data-stu-id="fd995-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="fd995-107">pro Ukazatel spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="fd995-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="fd995-108">szName</span><span class="sxs-lookup"><span data-stu-id="fd995-108">szName</span></span>  
 <span data-ttu-id="fd995-109">mimo Název typu.</span><span class="sxs-lookup"><span data-stu-id="fd995-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="fd995-110">mimo Počet znaků, které jsou k dispozici v bufferu řetězce.</span><span class="sxs-lookup"><span data-stu-id="fd995-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd995-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fd995-111">Remarks</span></span>  
 <span data-ttu-id="fd995-112">Pokud ve vlákně, které je aktuálně v kontextu, není žádný spravovaný kód, funkce vrátí hodnotu HRESULT SOS_E_NOMANAGEDCODE s hodnotou zařízení 0xa0 a kódem chyby 0x1000.</span><span class="sxs-lookup"><span data-stu-id="fd995-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd995-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fd995-113">Requirements</span></span>  
 <span data-ttu-id="fd995-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd995-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd995-115">**Hlavička:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="fd995-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="fd995-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd995-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd995-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd995-117">See also</span></span>

- [<span data-ttu-id="fd995-118">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="fd995-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
