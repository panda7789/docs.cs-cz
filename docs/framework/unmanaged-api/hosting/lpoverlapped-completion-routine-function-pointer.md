---
title: LPOVERLAPPED_COMPLETION_ROUTINE – ukazatel na funkci
ms.date: 03/30/2017
api_name:
- LPOVERLAPPED_COMPLETION_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59565b28991f6d61ff2c6c77540eace92461aa89
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490180"
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a><span data-ttu-id="ec7eb-102">LPOVERLAPPED_COMPLETION_ROUTINE – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="ec7eb-102">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>
<span data-ttu-id="ec7eb-103">Odkazuje na funkci, která upozorňuje hostitele, pokud překrytí (tj, asynchronní) vstupně-výstupních operací na zařízení byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="ec7eb-103">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="ec7eb-104">Tento ukazatel na funkci se již nepoužívá v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ec7eb-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec7eb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec7eb-105">Syntax</span></span>  
  
```  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec7eb-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec7eb-106">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="ec7eb-107">[in] Hodnotu, která je kód chyby, pokud bylo ukončeno zařízení; v opačném případě tato hodnota je nula.</span><span class="sxs-lookup"><span data-stu-id="ec7eb-107">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="ec7eb-108">Zavření zařízení způsobí, že všechny čekající vstupně-výstupních operací zařízení okamžitě provést.</span><span class="sxs-lookup"><span data-stu-id="ec7eb-108">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="ec7eb-109">[in] Počet bajtů přenesených vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="ec7eb-109">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="ec7eb-110">[in] Ukazatel na strukturu, která obsahuje informace, které se dá použít k dokončení žádosti o vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="ec7eb-110">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec7eb-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ec7eb-111">Remarks</span></span>  
 <span data-ttu-id="ec7eb-112">Funkce, které `LPOVERLAPPED_COMPLETION_ROUTINE` body je funkce zpětného volání a musí být implementováno tvůrci hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="ec7eb-112">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="ec7eb-113">Funkce zpětného volání umožňuje hostiteli zpracování dokončenou žádost vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="ec7eb-113">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec7eb-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ec7eb-114">Requirements</span></span>  
 <span data-ttu-id="ec7eb-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec7eb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec7eb-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ec7eb-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ec7eb-117">**Knihovna:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="ec7eb-117">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="ec7eb-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec7eb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec7eb-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec7eb-119">See also</span></span>

- [<span data-ttu-id="ec7eb-120">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="ec7eb-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
