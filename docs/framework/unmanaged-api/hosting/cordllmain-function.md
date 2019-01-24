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
ms.openlocfilehash: f62ad2c9ec6e1c9672ac5c78e838e926b02359f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512369"
---
# <a name="cordllmain-function"></a><span data-ttu-id="a87b7-102">_CorDllMain – funkce</span><span class="sxs-lookup"><span data-stu-id="a87b7-102">_CorDllMain Function</span></span>
<span data-ttu-id="a87b7-103">Inicializuje modul CLR (CLR), vyhledá spravovaný vstupní bod v záhlaví modulu CLR sestavení DLL a zahájí vykonávání.</span><span class="sxs-lookup"><span data-stu-id="a87b7-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a87b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a87b7-104">Syntax</span></span>  
  
```  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a87b7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a87b7-105">Parameters</span></span>  
 `hInst`  
 <span data-ttu-id="a87b7-106">[in] Popisovač instance načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="a87b7-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="a87b7-107">[in] Označuje, proč je volána funkce vstupního bodu knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="a87b7-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="a87b7-108">Tento parametr může být jeden z následujících hodnot: DLL_PROCESS_ATTACH, DLL_THREAD_ATTACH, DLL_THREAD_ATTACH nebo DLL_PROCESS_DETACH.</span><span class="sxs-lookup"><span data-stu-id="a87b7-108">This parameter can be one of the following values: DLL_PROCESS_ATTACH, DLL_THREAD_ATTACH, DLL_THREAD_ATTACH, or DLL_PROCESS_DETACH.</span></span> <span data-ttu-id="a87b7-109">Popisy těchto hodnot, najdete v článku `DllMain` dokumentaci Platform SDK.</span><span class="sxs-lookup"><span data-stu-id="a87b7-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="a87b7-110">[in] Nevyužité.</span><span class="sxs-lookup"><span data-stu-id="a87b7-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a87b7-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a87b7-111">Return Value</span></span>  
 <span data-ttu-id="a87b7-112">Tato metoda vrátí `true` k dosažení úspěchu a `false` Pokud dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="a87b7-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a87b7-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a87b7-113">Remarks</span></span>  
 <span data-ttu-id="a87b7-114">Tato funkce je volána zavaděčem operačního systému pro sestavení knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="a87b7-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="a87b7-115">Pro spustitelný soubor sestavení zavaděče volá [Funkce _CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) namísto toho funkci.</span><span class="sxs-lookup"><span data-stu-id="a87b7-115">For executable assemblies, the loader calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="a87b7-116">Zavaděč operačního systému volá tuto metodu, bez ohledu na vstupní bod uvedený v souboru knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="a87b7-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
 <span data-ttu-id="a87b7-117">Ve Windows 98, Windows ME, Windows NT a Windows 2000 `_CorDllMain` volána nepřímo prostřednictvím fixupin zavaděči operačního systému.</span><span class="sxs-lookup"><span data-stu-id="a87b7-117">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorDllMain` function is called indirectly through a fixupin the operating system loader.</span></span> <span data-ttu-id="a87b7-118">Ve všech ostatních verzích Windows je volána přímo zavaděčem operačního systému.</span><span class="sxs-lookup"><span data-stu-id="a87b7-118">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="a87b7-119">Další informace naleznete v části poznámky v [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="a87b7-119">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a87b7-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a87b7-120">Requirements</span></span>  
 <span data-ttu-id="a87b7-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a87b7-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a87b7-122">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a87b7-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a87b7-123">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a87b7-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a87b7-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a87b7-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a87b7-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a87b7-125">See also</span></span>
- [<span data-ttu-id="a87b7-126">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="a87b7-126">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
