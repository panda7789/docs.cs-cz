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
ms.openlocfilehash: 8c341d578a45d72804d9ac33e2aefe513fd33922
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="corexemain-function"></a><span data-ttu-id="9fab3-102">_CorExeMain – funkce</span><span class="sxs-lookup"><span data-stu-id="9fab3-102">_CorExeMain Function</span></span>
<span data-ttu-id="9fab3-103">Inicializuje modul CLR (CLR), vyhledá spravované vstupní bod v záhlaví modulu CLR spustitelný soubor sestavení a zahájí spuštění.</span><span class="sxs-lookup"><span data-stu-id="9fab3-103">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fab3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fab3-104">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="9fab3-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9fab3-105">Remarks</span></span>  
 <span data-ttu-id="9fab3-106">Tato funkce je volána zavaděčem v procesů vytvořených ze spravovaných sestavení spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="9fab3-106">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="9fab3-107">Pro knihovny DLL sestavení zavaděč volá [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) funkce místo.</span><span class="sxs-lookup"><span data-stu-id="9fab3-107">For DLL assemblies, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="9fab3-108">Zavaděč operačního systému volá tuto metodu, bez ohledu na to, vstupní bod uvedený v souboru bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="9fab3-108">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="9fab3-109">V systému Windows 98, Windows ME, systém Windows NT a Windows 2000 `_CorExeMain` funkce je volána nepřímo prostřednictvím oprava zavaděče operačního systému.</span><span class="sxs-lookup"><span data-stu-id="9fab3-109">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="9fab3-110">Ve všech ostatních verzí systému Windows je volána přímo zavaděčem operačního systému.</span><span class="sxs-lookup"><span data-stu-id="9fab3-110">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="9fab3-111">Další informace najdete v části poznámky v [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="9fab3-111">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fab3-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9fab3-112">Requirements</span></span>  
 <span data-ttu-id="9fab3-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fab3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fab3-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9fab3-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9fab3-115">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9fab3-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9fab3-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fab3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fab3-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="9fab3-117">See Also</span></span>  
 [<span data-ttu-id="9fab3-118">Globální statické funkce metadat</span><span class="sxs-lookup"><span data-stu-id="9fab3-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
