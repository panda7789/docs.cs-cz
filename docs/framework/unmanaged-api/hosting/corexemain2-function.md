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
ms.openlocfilehash: f968d84ae695eb1da127538ebdc5e4f55d6ebf39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985847"
---
# <a name="corexemain2-function"></a><span data-ttu-id="79e4f-102">_CorExeMain2 – funkce</span><span class="sxs-lookup"><span data-stu-id="79e4f-102">_CorExeMain2 Function</span></span>
<span data-ttu-id="79e4f-103">Spustí vstupní bod v zadané kódu mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="79e4f-103">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="79e4f-104">Tato funkce je volána zavaděčem operačního systému.</span><span class="sxs-lookup"><span data-stu-id="79e4f-104">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79e4f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79e4f-105">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79e4f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="79e4f-106">Parameters</span></span>  
 `pUnmappedPE`  
 <span data-ttu-id="79e4f-107">[in] Ukazatel na kódu mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="79e4f-107">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="79e4f-108">[in] Počet prvků, které `pUnmappedPE` může obsahovat.</span><span class="sxs-lookup"><span data-stu-id="79e4f-108">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="79e4f-109">[in] Ukazatel na název spustitelné bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="79e4f-109">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="79e4f-110">[in] Název souboru zavaděče.</span><span class="sxs-lookup"><span data-stu-id="79e4f-110">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="79e4f-111">[in] Parametry příkazového řádku, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="79e4f-111">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79e4f-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="79e4f-112">Requirements</span></span>  
 <span data-ttu-id="79e4f-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79e4f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79e4f-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="79e4f-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="79e4f-115">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="79e4f-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="79e4f-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79e4f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79e4f-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79e4f-117">See also</span></span>

- [<span data-ttu-id="79e4f-118">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="79e4f-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
