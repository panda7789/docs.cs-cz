---
title: "_CorExeMain – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: _CorExeMain
helpviewer_keywords: _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f5c0909db10c7bf8e15a7af998b78e0a193a908
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corexemain-function"></a><span data-ttu-id="51b15-102">_CorExeMain – funkce</span><span class="sxs-lookup"><span data-stu-id="51b15-102">_CorExeMain Function</span></span>
<span data-ttu-id="51b15-103">Inicializuje modul CLR (CLR), vyhledá spravované vstupní bod v záhlaví modulu CLR spustitelný soubor sestavení a zahájí spuštění.</span><span class="sxs-lookup"><span data-stu-id="51b15-103">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51b15-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51b15-104">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="51b15-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="51b15-105">Remarks</span></span>  
 <span data-ttu-id="51b15-106">Tato funkce je volána zavaděčem v procesů vytvořených ze spravovaných sestavení spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="51b15-106">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="51b15-107">Pro knihovny DLL sestavení zavaděč volá [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) funkce místo.</span><span class="sxs-lookup"><span data-stu-id="51b15-107">For DLL assemblies, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="51b15-108">Zavaděč operačního systému volá tuto metodu, bez ohledu na to, vstupní bod uvedený v souboru bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="51b15-108">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="51b15-109">V systému Windows 98, Windows ME, systém Windows NT a Windows 2000 `_CorExeMain` funkce je volána nepřímo prostřednictvím oprava zavaděče operačního systému.</span><span class="sxs-lookup"><span data-stu-id="51b15-109">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="51b15-110">Ve všech ostatních verzí systému Windows je volána přímo zavaděčem operačního systému.</span><span class="sxs-lookup"><span data-stu-id="51b15-110">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="51b15-111">Další informace najdete v části poznámky v [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="51b15-111">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51b15-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="51b15-112">Requirements</span></span>  
 <span data-ttu-id="51b15-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51b15-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51b15-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="51b15-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="51b15-115">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="51b15-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="51b15-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51b15-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51b15-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="51b15-117">See Also</span></span>  
 [<span data-ttu-id="51b15-118">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="51b15-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
