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
ms.openlocfilehash: cc5324683daa9a02a6a89b2a3fb57ee9fd5dbe72
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136952"
---
# <a name="_corexemain2-function"></a><span data-ttu-id="ea90a-102">_CorExeMain2 – funkce</span><span class="sxs-lookup"><span data-stu-id="ea90a-102">_CorExeMain2 Function</span></span>
<span data-ttu-id="ea90a-103">Provede vstupní bod v zadaném kódu mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="ea90a-103">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="ea90a-104">Tato funkce je volána zavaděčem operačního systému.</span><span class="sxs-lookup"><span data-stu-id="ea90a-104">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea90a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea90a-105">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea90a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea90a-106">Parameters</span></span>  
 `pUnmappedPE`  
 <span data-ttu-id="ea90a-107">pro Ukazatel na kód mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="ea90a-107">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="ea90a-108">pro Počet elementů, které `pUnmappedPE` může uchovávat.</span><span class="sxs-lookup"><span data-stu-id="ea90a-108">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="ea90a-109">pro Ukazatel na název spustitelného obrázku.</span><span class="sxs-lookup"><span data-stu-id="ea90a-109">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="ea90a-110">pro Název souboru zavaděče.</span><span class="sxs-lookup"><span data-stu-id="ea90a-110">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="ea90a-111">pro Parametry příkazového řádku, pokud existují.</span><span class="sxs-lookup"><span data-stu-id="ea90a-111">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea90a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ea90a-112">Requirements</span></span>  
 <span data-ttu-id="ea90a-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea90a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea90a-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ea90a-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ea90a-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ea90a-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ea90a-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea90a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea90a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea90a-117">See also</span></span>

- [<span data-ttu-id="ea90a-118">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="ea90a-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
