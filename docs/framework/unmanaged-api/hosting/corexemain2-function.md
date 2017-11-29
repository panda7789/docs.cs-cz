---
title: "_CorExeMain2 – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _CorExeMain2
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: _CorExeMain2
helpviewer_keywords: _CorExeMain2 function [.NET Framework hosting]
ms.assetid: 72ea68b4-689f-4733-9416-9664b75e8892
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7c705627de8e8157212ae3e6a2ab4f2c12246653
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="corexemain2-function"></a><span data-ttu-id="22615-102">_CorExeMain2 – funkce</span><span class="sxs-lookup"><span data-stu-id="22615-102">_CorExeMain2 Function</span></span>
<span data-ttu-id="22615-103">Vstupní bod se spustí v zadaný kód mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="22615-103">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="22615-104">Tato funkce je volána zavaděčem operačního systému.</span><span class="sxs-lookup"><span data-stu-id="22615-104">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22615-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22615-105">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="22615-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="22615-106">Parameters</span></span>  
 `pUnmappedPE`  
 <span data-ttu-id="22615-107">[v] Ukazatel na kód mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="22615-107">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="22615-108">[v] Počet elementů `pUnmappedPE` mohou být uloženy.</span><span class="sxs-lookup"><span data-stu-id="22615-108">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="22615-109">[v] Ukazatel na název spustitelné bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="22615-109">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="22615-110">[v] Název souboru zavaděč.</span><span class="sxs-lookup"><span data-stu-id="22615-110">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="22615-111">[v] Parametry příkazového řádku, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="22615-111">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22615-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22615-112">Requirements</span></span>  
 <span data-ttu-id="22615-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22615-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22615-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="22615-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="22615-115">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="22615-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="22615-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22615-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22615-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="22615-117">See Also</span></span>  
 [<span data-ttu-id="22615-118">Globální statické funkce metadat</span><span class="sxs-lookup"><span data-stu-id="22615-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
