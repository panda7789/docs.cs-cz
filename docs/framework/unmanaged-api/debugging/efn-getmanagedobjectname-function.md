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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4eddb1461ad448a1a1718db8a11173e5e2e4a17
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527780"
---
# <a name="efngetmanagedobjectname-function"></a><span data-ttu-id="4d19f-102">_EFN_GetManagedObjectName – funkce</span><span class="sxs-lookup"><span data-stu-id="4d19f-102">_EFN_GetManagedObjectName Function</span></span>
<span data-ttu-id="4d19f-103">Získá název typu pomocí ukazatele zadaný spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="4d19f-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d19f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d19f-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d19f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d19f-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="4d19f-106">[in] Ukazatel na klientovi ladění.</span><span class="sxs-lookup"><span data-stu-id="4d19f-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="4d19f-107">[in] Ukazatel spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="4d19f-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="4d19f-108">szName</span><span class="sxs-lookup"><span data-stu-id="4d19f-108">szName</span></span>  
 <span data-ttu-id="4d19f-109">[out] Název typu.</span><span class="sxs-lookup"><span data-stu-id="4d19f-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="4d19f-110">[out] Počet znaků, které jsou k dispozici ve vyrovnávací paměti řetězce.</span><span class="sxs-lookup"><span data-stu-id="4d19f-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d19f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d19f-111">Remarks</span></span>  
 <span data-ttu-id="4d19f-112">Pokud neexistuje žádný spravovaný kód ve vlákně aktuálně v kontextu, funkce vrátí HRESULT SOS_E_NOMANAGEDCODE s hodnotou zařízení 0xa0 a 0x1000 kód chyby.</span><span class="sxs-lookup"><span data-stu-id="4d19f-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d19f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d19f-113">Requirements</span></span>  
 <span data-ttu-id="4d19f-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d19f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d19f-115">**Záhlaví:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="4d19f-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="4d19f-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d19f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d19f-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d19f-117">See also</span></span>
- [<span data-ttu-id="4d19f-118">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="4d19f-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
