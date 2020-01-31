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
ms.openlocfilehash: 9230e1fcba7c0492e50773e7ca13fb16f07238a2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789139"
---
# <a name="_efn_getmanagedobjectname-function"></a><span data-ttu-id="f1e94-102">\_EFN\_GetManagedObjectName Function</span><span class="sxs-lookup"><span data-stu-id="f1e94-102">\_EFN\_GetManagedObjectName Function</span></span>
<span data-ttu-id="f1e94-103">Získá název typu pomocí zadaného ukazatele spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="f1e94-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1e94-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1e94-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1e94-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1e94-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="f1e94-106">pro Ukazatel na ladicího klienta.</span><span class="sxs-lookup"><span data-stu-id="f1e94-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="f1e94-107">pro Ukazatel spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="f1e94-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="f1e94-108">szName</span><span class="sxs-lookup"><span data-stu-id="f1e94-108">szName</span></span>  
 <span data-ttu-id="f1e94-109">mimo Název typu.</span><span class="sxs-lookup"><span data-stu-id="f1e94-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="f1e94-110">mimo Počet znaků, které jsou k dispozici v bufferu řetězce.</span><span class="sxs-lookup"><span data-stu-id="f1e94-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1e94-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f1e94-111">Remarks</span></span>  
 <span data-ttu-id="f1e94-112">Pokud ve vlákně, který je aktuálně v kontextu, není žádný spravovaný kód, funkce vrátí hodnotu HRESULT SOS_E_NOMANAGEDCODE s hodnotou zařízení 0xa0 a kódem chyby 0x1000.</span><span class="sxs-lookup"><span data-stu-id="f1e94-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1e94-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f1e94-113">Requirements</span></span>  
 <span data-ttu-id="f1e94-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1e94-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1e94-115">**Hlavička:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="f1e94-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="f1e94-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1e94-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1e94-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1e94-117">See also</span></span>

- [<span data-ttu-id="f1e94-118">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="f1e94-118">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
