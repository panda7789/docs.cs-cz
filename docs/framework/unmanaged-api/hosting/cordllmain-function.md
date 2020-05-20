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
ms.openlocfilehash: 3b2322f708afed08172f87e843c225aa9c60d9d3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616603"
---
# <a name="_cordllmain-function"></a><span data-ttu-id="3e833-102">\_CorDllMain – funkce</span><span class="sxs-lookup"><span data-stu-id="3e833-102">\_CorDllMain Function</span></span>

<span data-ttu-id="3e833-103">Inicializuje modul CLR (Common Language Runtime), vyhledá spravovaný vstupní bod v záhlaví modulu CLR sestavení knihovny DLL a zahájí provádění.</span><span class="sxs-lookup"><span data-stu-id="3e833-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e833-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e833-104">Syntax</span></span>  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e833-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e833-105">Parameters</span></span>  
 `hInst`  
 <span data-ttu-id="3e833-106">pro Obslužná rutina instance načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="3e833-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="3e833-107">pro Určuje, proč je volána funkce vstupního bodu knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="3e833-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="3e833-108">Tento parametr může být jedna z následujících hodnot: DLL \_ PROCESS_ATTACH, \_ připojení vlákna dll \_ , \_ připojení vlákna DLL \_ nebo \_ odpojení procesu dll \_ .</span><span class="sxs-lookup"><span data-stu-id="3e833-108">This parameter can be one of the following values: DLL\_PROCESS_ATTACH, DLL\_THREAD\_ATTACH, DLL\_THREAD\_ATTACH, or DLL\_PROCESS\_DETACH.</span></span> <span data-ttu-id="3e833-109">Popisy těchto hodnot naleznete v `DllMain` dokumentaci k sadě SDK platformy.</span><span class="sxs-lookup"><span data-stu-id="3e833-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="3e833-110">pro Nepoužívané.</span><span class="sxs-lookup"><span data-stu-id="3e833-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e833-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3e833-111">Return Value</span></span>  
 <span data-ttu-id="3e833-112">Tato metoda `true` se vrátí pro úspěch a `false` dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="3e833-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e833-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e833-113">Remarks</span></span>  
 <span data-ttu-id="3e833-114">Tato funkce je volána zavaděčem operačního systému pro sestavení knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="3e833-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="3e833-115">V případě spustitelných sestavení volá zavaděč místo toho funkci [ \_ CorExeMain](corexemain-function.md) .</span><span class="sxs-lookup"><span data-stu-id="3e833-115">For executable assemblies, the loader calls the [\_CorExeMain](corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="3e833-116">Zavaděč operačního systému volá tuto metodu bez ohledu na vstupní bod zadaný v souboru DLL.</span><span class="sxs-lookup"><span data-stu-id="3e833-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
<span data-ttu-id="3e833-117">`_CorDllMain`Funkce je volána přímo zavaděčem operačního systému.</span><span class="sxs-lookup"><span data-stu-id="3e833-117">The `_CorDllMain` function is called directly by the operating system loader.</span></span>
  
 <span data-ttu-id="3e833-118">Další informace najdete v části poznámky v tématu [ \_ CorValidateImage](corvalidateimage-function.md) .</span><span class="sxs-lookup"><span data-stu-id="3e833-118">For additional information, see the Remarks section in the [\_CorValidateImage](corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e833-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e833-119">Requirements</span></span>  

 <span data-ttu-id="3e833-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e833-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e833-121">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3e833-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3e833-122">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3e833-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3e833-123">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e833-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e833-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e833-124">See also</span></span>

- [<span data-ttu-id="3e833-125">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="3e833-125">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
