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
ms.openlocfilehash: 103ac75e7c3eaf9739c3a448ff1c052c158621db
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090906"
---
# <a name="lpoverlapped_completion_routine-function-pointer"></a><span data-ttu-id="999ef-102">LPOVERLAPPED_COMPLETION_ROUTINE – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="999ef-102">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>
<span data-ttu-id="999ef-103">Odkazuje na funkci, která upozorňuje hostitele, když je dokončeno překrytí (tj. asynchronní) vstupně-výstupní operace se zařízením.</span><span class="sxs-lookup"><span data-stu-id="999ef-103">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="999ef-104">Tento ukazatel funkce je zastaralý v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="999ef-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="999ef-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="999ef-105">Syntax</span></span>  
  
```cpp  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="999ef-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="999ef-106">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="999ef-107">pro Hodnota, která je kód chyby v případě, že zařízení bylo zavřeno; v opačném případě je tato hodnota nulová.</span><span class="sxs-lookup"><span data-stu-id="999ef-107">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="999ef-108">Když se zařízení uzavírá, způsobí to okamžité dokončení všech nedokončených vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="999ef-108">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="999ef-109">pro Počet bajtů přenesených operací I/O.</span><span class="sxs-lookup"><span data-stu-id="999ef-109">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="999ef-110">pro Ukazatel na strukturu, která obsahuje informace, které se mají použít k dokončení vstupně-výstupních požadavků.</span><span class="sxs-lookup"><span data-stu-id="999ef-110">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="999ef-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="999ef-111">Remarks</span></span>  
 <span data-ttu-id="999ef-112">Funkce, na kterou `LPOVERLAPPED_COMPLETION_ROUTINE` body, je funkce zpětného volání a musí být implementována zapisovačí hostující aplikace.</span><span class="sxs-lookup"><span data-stu-id="999ef-112">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="999ef-113">Funkce zpětného volání umožňuje hostiteli zpracovat dokončenou vstupně-výstupní žádost.</span><span class="sxs-lookup"><span data-stu-id="999ef-113">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="999ef-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="999ef-114">Requirements</span></span>  
 <span data-ttu-id="999ef-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="999ef-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="999ef-116">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="999ef-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="999ef-117">**Knihovna:** Knihovny Mscorwks. dll</span><span class="sxs-lookup"><span data-stu-id="999ef-117">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="999ef-118">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="999ef-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="999ef-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="999ef-119">See also</span></span>

- [<span data-ttu-id="999ef-120">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="999ef-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
