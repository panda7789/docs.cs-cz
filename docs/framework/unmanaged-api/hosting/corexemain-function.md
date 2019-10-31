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
ms.openlocfilehash: 8541e7761e2f8e1839d028fdaea3eb71307ba615
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131203"
---
# <a name="_corexemain-function"></a><span data-ttu-id="7abba-102">_CorExeMain – funkce</span><span class="sxs-lookup"><span data-stu-id="7abba-102">_CorExeMain Function</span></span>
<span data-ttu-id="7abba-103">Inicializuje modul CLR (Common Language Runtime), vyhledá spravovaný vstupní bod v záhlaví modulu CLR spustitelného sestavení a zahájí provádění.</span><span class="sxs-lookup"><span data-stu-id="7abba-103">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7abba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7abba-104">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="7abba-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7abba-105">Remarks</span></span>  
 <span data-ttu-id="7abba-106">Tato funkce je volána zavaděčem v procesech vytvořených ze spravovaných spustitelných sestavení.</span><span class="sxs-lookup"><span data-stu-id="7abba-106">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="7abba-107">Pro sestavení knihoven DLL volá zavaděč funkci [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) .</span><span class="sxs-lookup"><span data-stu-id="7abba-107">For DLL assemblies, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="7abba-108">Zavaděč operačního systému volá tuto metodu bez ohledu na vstupní bod zadaný v souboru obrázku.</span><span class="sxs-lookup"><span data-stu-id="7abba-108">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="7abba-109">V systémech Windows 98, Windows MILLENNIUM, Windows NT a Windows 2000 je funkce `_CorExeMain` volána nepřímo prostřednictvím opravy v zavaděči operačního systému.</span><span class="sxs-lookup"><span data-stu-id="7abba-109">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="7abba-110">Ve všech ostatních verzích systému Windows je volána přímo zavaděčem operačního systému.</span><span class="sxs-lookup"><span data-stu-id="7abba-110">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="7abba-111">Další informace najdete v části poznámky v tématu [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) .</span><span class="sxs-lookup"><span data-stu-id="7abba-111">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7abba-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7abba-112">Requirements</span></span>  
 <span data-ttu-id="7abba-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7abba-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7abba-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7abba-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7abba-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7abba-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7abba-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7abba-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7abba-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7abba-117">See also</span></span>

- [<span data-ttu-id="7abba-118">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="7abba-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
