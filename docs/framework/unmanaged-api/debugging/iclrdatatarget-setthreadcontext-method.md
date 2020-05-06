---
title: ICLRDataTarget::SetThreadContext – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetThreadContext
helpviewer_keywords:
- SetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::SetThreadContext method [.NET Framework debugging]
ms.assetid: 103c8502-81fe-40d7-9c1e-9008d8fb19e1
topic_type:
- apiref
ms.openlocfilehash: b8c4b4e585bba4df39a743273221f38ce14a9b9d
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860529"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="218db-102">ICLRDataTarget::SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="218db-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="218db-103">Nastaví aktuální kontext zadaného vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="218db-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="218db-104">Tato metoda je volána službou Common Language Runtime (CLR) pro přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="218db-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="218db-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="218db-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="218db-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="218db-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="218db-107">pro Identifikátor operačního systému vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="218db-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="218db-108">pro Velikost kontextu.</span><span class="sxs-lookup"><span data-stu-id="218db-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="218db-109">pro Ukazatel na vyrovnávací paměť obsahující kontext.</span><span class="sxs-lookup"><span data-stu-id="218db-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="218db-110">Data ve `context` vyrovnávací paměti budou v podobě struktury Win32 `CONTEXT` .</span><span class="sxs-lookup"><span data-stu-id="218db-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="218db-111">Kontext určuje data registru specifická pro procesor, takže definice struktury Win32 `CONTEXT` závisí na architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="218db-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="218db-112">Definici struktury Win32 `CONTEXT` najdete v souboru hlaviček Winnt. h.</span><span class="sxs-lookup"><span data-stu-id="218db-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="218db-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="218db-113">Remarks</span></span>  
 <span data-ttu-id="218db-114">Tato metoda je implementována modulem pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="218db-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="218db-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="218db-115">Requirements</span></span>  
 <span data-ttu-id="218db-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="218db-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="218db-117">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="218db-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="218db-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="218db-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="218db-119">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="218db-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="218db-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="218db-120">See also</span></span>

- [<span data-ttu-id="218db-121">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="218db-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
