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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a02a899fd6fbffd04ef25913adb6a65ade27177
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755656"
---
# <a name="cordllmain-function"></a><span data-ttu-id="91251-102">\_CorDllMain Function</span><span class="sxs-lookup"><span data-stu-id="91251-102">\_CorDllMain Function</span></span>

<span data-ttu-id="91251-103">Inicializuje modul CLR (CLR), vyhledá spravovaný vstupní bod v záhlaví modulu CLR sestavení DLL a zahájí vykonávání.</span><span class="sxs-lookup"><span data-stu-id="91251-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91251-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91251-104">Syntax</span></span>  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91251-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91251-105">Parameters</span></span>  
 `hInst`  
 <span data-ttu-id="91251-106">[in] Popisovač instance načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="91251-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="91251-107">[in] Označuje, proč je volána funkce vstupního bodu knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="91251-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="91251-108">Tento parametr může být jeden z následujících hodnot: Knihovna DLL\_PROCESS_ATTACH, knihovny DLL\_vlákna\_připojit, knihovny DLL\_vlákna\_ATTACH nebo knihovny DLL\_procesu\_ODPOJIT.</span><span class="sxs-lookup"><span data-stu-id="91251-108">This parameter can be one of the following values: DLL\_PROCESS_ATTACH, DLL\_THREAD\_ATTACH, DLL\_THREAD\_ATTACH, or DLL\_PROCESS\_DETACH.</span></span> <span data-ttu-id="91251-109">Popisy těchto hodnot, najdete v článku `DllMain` dokumentaci Platform SDK.</span><span class="sxs-lookup"><span data-stu-id="91251-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="91251-110">[in] Nevyužité.</span><span class="sxs-lookup"><span data-stu-id="91251-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91251-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="91251-111">Return Value</span></span>  
 <span data-ttu-id="91251-112">Tato metoda vrátí `true` k dosažení úspěchu a `false` Pokud dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="91251-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91251-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="91251-113">Remarks</span></span>  
 <span data-ttu-id="91251-114">Tato funkce je volána zavaděčem operačního systému pro sestavení knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="91251-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="91251-115">Pro spustitelný soubor sestavení zavaděče volá [ \_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) namísto toho funkci.</span><span class="sxs-lookup"><span data-stu-id="91251-115">For executable assemblies, the loader calls the [\_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="91251-116">Zavaděč operačního systému volá tuto metodu, bez ohledu na vstupní bod uvedený v souboru knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="91251-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
<span data-ttu-id="91251-117">`_CorDllMain` Funkce je volána přímo zavaděčem operačního systému.</span><span class="sxs-lookup"><span data-stu-id="91251-117">The `_CorDllMain` function is called directly by the operating system loader.</span></span>
  
 <span data-ttu-id="91251-118">Další informace naleznete v části poznámky v [ \_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="91251-118">For additional information, see the Remarks section in the [\_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91251-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91251-119">Requirements</span></span>  

 <span data-ttu-id="91251-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91251-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91251-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="91251-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="91251-122">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="91251-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="91251-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91251-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91251-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91251-124">See also</span></span>

- [<span data-ttu-id="91251-125">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="91251-125">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
