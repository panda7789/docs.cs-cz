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
ms.openlocfilehash: 63af5979b113f81c01c9c68d6cccdfa10811265a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429131"
---
# <a name="corexemain-function"></a><span data-ttu-id="c26f1-102">_CorExeMain – funkce</span><span class="sxs-lookup"><span data-stu-id="c26f1-102">_CorExeMain Function</span></span>
<span data-ttu-id="c26f1-103">Inicializuje modul CLR (CLR), vyhledá spravované vstupní bod v záhlaví modulu CLR spustitelný soubor sestavení a zahájí spuštění.</span><span class="sxs-lookup"><span data-stu-id="c26f1-103">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c26f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c26f1-104">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c26f1-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c26f1-105">Remarks</span></span>  
 <span data-ttu-id="c26f1-106">Tato funkce je volána zavaděčem v procesů vytvořených ze spravovaných sestavení spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="c26f1-106">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="c26f1-107">Pro knihovny DLL sestavení zavaděč volá [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) funkce místo.</span><span class="sxs-lookup"><span data-stu-id="c26f1-107">For DLL assemblies, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="c26f1-108">Zavaděč operačního systému volá tuto metodu, bez ohledu na to, vstupní bod uvedený v souboru bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="c26f1-108">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="c26f1-109">V systému Windows 98, Windows ME, systém Windows NT a Windows 2000 `_CorExeMain` funkce je volána nepřímo prostřednictvím oprava zavaděče operačního systému.</span><span class="sxs-lookup"><span data-stu-id="c26f1-109">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="c26f1-110">Ve všech ostatních verzí systému Windows je volána přímo zavaděčem operačního systému.</span><span class="sxs-lookup"><span data-stu-id="c26f1-110">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="c26f1-111">Další informace najdete v části poznámky v [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="c26f1-111">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c26f1-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c26f1-112">Requirements</span></span>  
 <span data-ttu-id="c26f1-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c26f1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c26f1-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c26f1-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c26f1-115">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c26f1-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c26f1-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c26f1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c26f1-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="c26f1-117">See Also</span></span>  
 [<span data-ttu-id="c26f1-118">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="c26f1-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
