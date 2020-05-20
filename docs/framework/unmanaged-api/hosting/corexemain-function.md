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
ms.openlocfilehash: 935ac478fb966315e81fdcc004761038b28e3178
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616587"
---
# <a name="_corexemain-function"></a><span data-ttu-id="9e4cf-102">_CorExeMain – funkce</span><span class="sxs-lookup"><span data-stu-id="9e4cf-102">_CorExeMain Function</span></span>
<span data-ttu-id="9e4cf-103">Inicializuje modul CLR (Common Language Runtime), vyhledá spravovaný vstupní bod v záhlaví modulu CLR spustitelného sestavení a zahájí provádění.</span><span class="sxs-lookup"><span data-stu-id="9e4cf-103">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e4cf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e4cf-104">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="9e4cf-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e4cf-105">Remarks</span></span>  
 <span data-ttu-id="9e4cf-106">Tato funkce je volána zavaděčem v procesech vytvořených ze spravovaných spustitelných sestavení.</span><span class="sxs-lookup"><span data-stu-id="9e4cf-106">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="9e4cf-107">Pro sestavení knihovny DLL volá zavaděč místo toho funkci [_CorDllMain](cordllmain-function.md) .</span><span class="sxs-lookup"><span data-stu-id="9e4cf-107">For DLL assemblies, the loader calls the [_CorDllMain](cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="9e4cf-108">Zavaděč operačního systému volá tuto metodu bez ohledu na vstupní bod zadaný v souboru obrázku.</span><span class="sxs-lookup"><span data-stu-id="9e4cf-108">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="9e4cf-109">V systémech Windows 98, Windows MILLENNIUM, Windows NT a Windows 2000 `_CorExeMain` je funkce volána nepřímo prostřednictvím opravy v zavaděči operačního systému.</span><span class="sxs-lookup"><span data-stu-id="9e4cf-109">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="9e4cf-110">Ve všech ostatních verzích systému Windows je volána přímo zavaděčem operačního systému.</span><span class="sxs-lookup"><span data-stu-id="9e4cf-110">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="9e4cf-111">Další informace najdete v části poznámky v tématu [_CorValidateImage](corvalidateimage-function.md) .</span><span class="sxs-lookup"><span data-stu-id="9e4cf-111">For additional information, see the Remarks section in the [_CorValidateImage](corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e4cf-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e4cf-112">Requirements</span></span>  
 <span data-ttu-id="9e4cf-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e4cf-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e4cf-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9e4cf-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9e4cf-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9e4cf-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9e4cf-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e4cf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e4cf-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e4cf-117">See also</span></span>

- [<span data-ttu-id="9e4cf-118">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="9e4cf-118">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
