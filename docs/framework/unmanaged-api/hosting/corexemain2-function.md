---
title: _CorExeMain2 – funkce
ms.date: 03/30/2017
api_name:
- _CorExeMain2
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain2
helpviewer_keywords:
- _CorExeMain2 function [.NET Framework hosting]
ms.assetid: 72ea68b4-689f-4733-9416-9664b75e8892
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 573336b32040f44ff1b59fcbb75b59aa00976b5c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430176"
---
# <a name="corexemain2-function"></a><span data-ttu-id="c1b4b-102">_CorExeMain2 – funkce</span><span class="sxs-lookup"><span data-stu-id="c1b4b-102">_CorExeMain2 Function</span></span>
<span data-ttu-id="c1b4b-103">Vstupní bod se spustí v zadaný kód mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="c1b4b-103">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="c1b4b-104">Tato funkce je volána zavaděčem operačního systému.</span><span class="sxs-lookup"><span data-stu-id="c1b4b-104">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1b4b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1b4b-105">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1b4b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1b4b-106">Parameters</span></span>  
 `pUnmappedPE`  
 <span data-ttu-id="c1b4b-107">[v] Ukazatel na kód mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="c1b4b-107">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="c1b4b-108">[v] Počet elementů `pUnmappedPE` mohou být uloženy.</span><span class="sxs-lookup"><span data-stu-id="c1b4b-108">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="c1b4b-109">[v] Ukazatel na název spustitelné bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="c1b4b-109">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="c1b4b-110">[v] Název souboru zavaděč.</span><span class="sxs-lookup"><span data-stu-id="c1b4b-110">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="c1b4b-111">[v] Parametry příkazového řádku, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="c1b4b-111">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1b4b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c1b4b-112">Requirements</span></span>  
 <span data-ttu-id="c1b4b-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1b4b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1b4b-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c1b4b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c1b4b-115">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c1b4b-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c1b4b-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1b4b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1b4b-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1b4b-117">See Also</span></span>  
 [<span data-ttu-id="c1b4b-118">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="c1b4b-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
