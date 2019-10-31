---
title: _CorDllMain – funkce
ms.date: 03/30/2017
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
ms.openlocfilehash: f60f159ab4770023cee7123b39109040243e1ccd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136969"
---
# <a name="_cordllmain-function"></a><span data-ttu-id="4ce92-102">\_funkce CorDllMain</span><span class="sxs-lookup"><span data-stu-id="4ce92-102">\_CorDllMain Function</span></span>

<span data-ttu-id="4ce92-103">Inicializuje modul CLR (Common Language Runtime), vyhledá spravovaný vstupní bod v záhlaví modulu CLR sestavení knihovny DLL a zahájí provádění.</span><span class="sxs-lookup"><span data-stu-id="4ce92-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ce92-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ce92-104">Syntax</span></span>  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ce92-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ce92-105">Parameters</span></span>  
 `hInst`  
 <span data-ttu-id="4ce92-106">pro Obslužná rutina instance načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="4ce92-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="4ce92-107">pro Určuje, proč je volána funkce vstupního bodu knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="4ce92-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="4ce92-108">Tento parametr může být jedna z následujících hodnot: DLL\_PROCESS_ATTACH, DLL\_vlákna\_připojit, DLL\_vlákna\_připojit nebo knihovny DLL\_proces\_odpojení.</span><span class="sxs-lookup"><span data-stu-id="4ce92-108">This parameter can be one of the following values: DLL\_PROCESS_ATTACH, DLL\_THREAD\_ATTACH, DLL\_THREAD\_ATTACH, or DLL\_PROCESS\_DETACH.</span></span> <span data-ttu-id="4ce92-109">Popisy těchto hodnot naleznete v dokumentaci k `DllMain` v sadě SDK platformy.</span><span class="sxs-lookup"><span data-stu-id="4ce92-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="4ce92-110">pro Nepoužívané.</span><span class="sxs-lookup"><span data-stu-id="4ce92-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ce92-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4ce92-111">Return Value</span></span>  
 <span data-ttu-id="4ce92-112">Tato metoda vrací `true` pro úspěch a `false`, pokud dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="4ce92-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ce92-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4ce92-113">Remarks</span></span>  
 <span data-ttu-id="4ce92-114">Tato funkce je volána zavaděčem operačního systému pro sestavení knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="4ce92-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="4ce92-115">U spustitelných sestavení volá zavaděč místo toho funkci [\_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) .</span><span class="sxs-lookup"><span data-stu-id="4ce92-115">For executable assemblies, the loader calls the [\_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="4ce92-116">Zavaděč operačního systému volá tuto metodu bez ohledu na vstupní bod zadaný v souboru DLL.</span><span class="sxs-lookup"><span data-stu-id="4ce92-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
<span data-ttu-id="4ce92-117">Funkce `_CorDllMain` je volána přímo zavaděčem operačního systému.</span><span class="sxs-lookup"><span data-stu-id="4ce92-117">The `_CorDllMain` function is called directly by the operating system loader.</span></span>
  
 <span data-ttu-id="4ce92-118">Další informace najdete v části poznámky v tématu [\_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) .</span><span class="sxs-lookup"><span data-stu-id="4ce92-118">For additional information, see the Remarks section in the [\_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ce92-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4ce92-119">Requirements</span></span>  

 <span data-ttu-id="4ce92-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ce92-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ce92-121">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4ce92-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4ce92-122">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4ce92-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4ce92-123">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ce92-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ce92-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ce92-124">See also</span></span>

- [<span data-ttu-id="4ce92-125">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="4ce92-125">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
