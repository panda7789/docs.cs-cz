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
ms.openlocfilehash: 8202fe4ec3ae6ef96440f203c5aea6db84744a72
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616577"
---
# <a name="_corexemain2-function"></a><span data-ttu-id="c8836-102">_CorExeMain2 – funkce</span><span class="sxs-lookup"><span data-stu-id="c8836-102">_CorExeMain2 Function</span></span>
<span data-ttu-id="c8836-103">Provede vstupní bod v zadaném kódu mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="c8836-103">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="c8836-104">Tato funkce je volána zavaděčem operačního systému.</span><span class="sxs-lookup"><span data-stu-id="c8836-104">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8836-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8836-105">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8836-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8836-106">Parameters</span></span>  
 `pUnmappedPE`  
 <span data-ttu-id="c8836-107">pro Ukazatel na kód mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="c8836-107">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="c8836-108">pro Počet elementů `pUnmappedPE` může obsahovat.</span><span class="sxs-lookup"><span data-stu-id="c8836-108">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="c8836-109">pro Ukazatel na název spustitelného obrázku.</span><span class="sxs-lookup"><span data-stu-id="c8836-109">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="c8836-110">pro Název souboru zavaděče.</span><span class="sxs-lookup"><span data-stu-id="c8836-110">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="c8836-111">pro Parametry příkazového řádku, pokud existují.</span><span class="sxs-lookup"><span data-stu-id="c8836-111">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8836-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8836-112">Requirements</span></span>  
 <span data-ttu-id="c8836-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8836-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8836-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c8836-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c8836-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c8836-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c8836-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8836-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8836-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8836-117">See also</span></span>

- [<span data-ttu-id="c8836-118">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="c8836-118">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
