---
title: "_EFN_GetManagedObjectName – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _EFN_GetManagedObjectName
api_location: mscordbi.dll
api_type: COM
f1_keywords: _EFN_GetManagedObjectName
helpviewer_keywords: _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 80e36f6c60c4c305cad9176cd7f185d8b6d2fdf2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="efngetmanagedobjectname-function"></a><span data-ttu-id="c243a-102">_EFN_GetManagedObjectName – funkce</span><span class="sxs-lookup"><span data-stu-id="c243a-102">_EFN_GetManagedObjectName Function</span></span>
<span data-ttu-id="c243a-103">Získá název typu pomocí ukazatele zadaný spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="c243a-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c243a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c243a-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c243a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c243a-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="c243a-106">[v] Ukazatel na klientské ladění.</span><span class="sxs-lookup"><span data-stu-id="c243a-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="c243a-107">[v] Ukazatel spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="c243a-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="c243a-108">szName</span><span class="sxs-lookup"><span data-stu-id="c243a-108">szName</span></span>  
 <span data-ttu-id="c243a-109">[out] Název typu.</span><span class="sxs-lookup"><span data-stu-id="c243a-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="c243a-110">[out] Počet znaků, které jsou k dispozici ve vyrovnávací paměti řetězců.</span><span class="sxs-lookup"><span data-stu-id="c243a-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c243a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c243a-111">Remarks</span></span>  
 <span data-ttu-id="c243a-112">Pokud neexistuje žádný spravovaný kód ve vlákně aktuálně v kontextu, funkce vrátí HRESULT SOS_E_NOMANAGEDCODE s hodnotou zařízení 0xa0 a chybový kód 0x1000.</span><span class="sxs-lookup"><span data-stu-id="c243a-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c243a-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c243a-113">Requirements</span></span>  
 <span data-ttu-id="c243a-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c243a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c243a-115">**Záhlaví:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="c243a-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="c243a-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c243a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c243a-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="c243a-117">See Also</span></span>  
 [<span data-ttu-id="c243a-118">Globální statické funkce ladění</span><span class="sxs-lookup"><span data-stu-id="c243a-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
