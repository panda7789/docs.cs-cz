---
title: "LPOVERLAPPED_COMPLETION_ROUTINE – ukazatel na funkci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LPOVERLAPPED_COMPLETION_ROUTINE
api_location: mscoree.dll
api_type: COM
f1_keywords: LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords: LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4d50f2058796d4c5c900474cdcbe71d8a5a911ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a><span data-ttu-id="e2529-102">LPOVERLAPPED_COMPLETION_ROUTINE – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="e2529-102">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>
<span data-ttu-id="e2529-103">Odkazuje na funkci, která upozorní hostitele, když překryté (tedy asynchronní) vstupně-výstupních operací na zařízení byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="e2529-103">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="e2529-104">Tento ukazatel na funkci se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e2529-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2529-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2529-105">Syntax</span></span>  
  
```  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2529-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2529-106">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="e2529-107">[v] Hodnotu, která je kód chyby, pokud bylo ukončeno zařízení; Tato hodnota je, jinak hodnota nula.</span><span class="sxs-lookup"><span data-stu-id="e2529-107">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="e2529-108">Zavření zařízení způsobí, že všechna nevyřízená vstupně-výstupních operací na zařízení provést okamžitě.</span><span class="sxs-lookup"><span data-stu-id="e2529-108">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="e2529-109">[v] Počet bajtů přenesených vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="e2529-109">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="e2529-110">[v] Ukazatel na strukturu, která obsahuje informace, které umožňuje dokončit požadavek na vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="e2529-110">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2529-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2529-111">Remarks</span></span>  
 <span data-ttu-id="e2529-112">Funkce, ke kterému `LPOVERLAPPED_COMPLETION_ROUTINE` body je funkce zpětného volání a musí být implementována zapisovačem hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e2529-112">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="e2529-113">Funkce zpětného volání umožňuje hostiteli zpracovat dokončenou žádost vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="e2529-113">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2529-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2529-114">Requirements</span></span>  
 <span data-ttu-id="e2529-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2529-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2529-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e2529-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e2529-117">**Knihovna:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="e2529-117">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="e2529-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2529-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2529-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2529-119">See Also</span></span>  
 [<span data-ttu-id="e2529-120">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="e2529-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
