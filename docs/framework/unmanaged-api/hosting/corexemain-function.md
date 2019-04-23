---
title: _CorExeMain – funkce
ms.date: 03/30/2017
api_name:
- _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain
helpviewer_keywords:
- _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7407db297a827004c851b904b2da8652778cb08
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177486"
---
# <a name="corexemain-function"></a><span data-ttu-id="071b0-102">_CorExeMain – funkce</span><span class="sxs-lookup"><span data-stu-id="071b0-102">_CorExeMain Function</span></span>
<span data-ttu-id="071b0-103">Inicializuje modul CLR (CLR), vyhledá spravovaný vstupní bod v záhlaví spustitelného sestavení modulu CLR a zahájí vykonávání.</span><span class="sxs-lookup"><span data-stu-id="071b0-103">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="071b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="071b0-104">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="071b0-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="071b0-105">Remarks</span></span>  
 <span data-ttu-id="071b0-106">Tato funkce je volána zavaděčem v procesů vytvořených ze spravovaných sestavení spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="071b0-106">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="071b0-107">Pro sestavení knihovny DLL, volání zavaděče [_cordllmain –](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) namísto toho funkci.</span><span class="sxs-lookup"><span data-stu-id="071b0-107">For DLL assemblies, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="071b0-108">Zavaděč operačního systému volá tuto metodu, bez ohledu na vstupní bod uvedený v souboru bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="071b0-108">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="071b0-109">Ve Windows 98, Windows ME, Windows NT a Windows 2000 `_CorExeMain` funkce se volá nepřímo prostřednictvím opravy v zavaděči operačního systému.</span><span class="sxs-lookup"><span data-stu-id="071b0-109">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="071b0-110">Ve všech ostatních verzích Windows je volána přímo zavaděčem operačního systému.</span><span class="sxs-lookup"><span data-stu-id="071b0-110">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="071b0-111">Další informace naleznete v části poznámky v [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="071b0-111">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="071b0-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="071b0-112">Requirements</span></span>  
 <span data-ttu-id="071b0-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="071b0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="071b0-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="071b0-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="071b0-115">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="071b0-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="071b0-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="071b0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="071b0-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="071b0-117">See also</span></span>

- [<span data-ttu-id="071b0-118">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="071b0-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
