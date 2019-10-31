---
title: CreateApplicationContext – funkce
ms.date: 03/30/2017
api_name:
- CreateApplicationContext
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateApplicationContext
helpviewer_keywords:
- CreateApplicationContext function [.NET Framework fusion]
ms.assetid: 7bf8a141-b2c0-4058-9885-1cef7dcaa811
topic_type:
- apiref
ms.openlocfilehash: e188fe80e770481aac02244a2c105639e4da19e2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108893"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="ef6ea-102">CreateApplicationContext – funkce</span><span class="sxs-lookup"><span data-stu-id="ef6ea-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="ef6ea-103">Tato funkce podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="ef6ea-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef6ea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef6ea-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef6ea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef6ea-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="ef6ea-106">pro Ukazatel na popisný název.</span><span class="sxs-lookup"><span data-stu-id="ef6ea-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="ef6ea-107">mimo Ukazatel na kontext aplikace.</span><span class="sxs-lookup"><span data-stu-id="ef6ea-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef6ea-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ef6ea-108">Requirements</span></span>  
 <span data-ttu-id="ef6ea-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef6ea-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef6ea-110">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="ef6ea-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ef6ea-111">**Knihovna:** Zahrnuto jako prostředek v Fusion. dll</span><span class="sxs-lookup"><span data-stu-id="ef6ea-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="ef6ea-112">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef6ea-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef6ea-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef6ea-113">See also</span></span>

- [<span data-ttu-id="ef6ea-114">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ef6ea-114">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="ef6ea-115">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="ef6ea-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="ef6ea-116">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="ef6ea-116">Global Assembly Cache</span></span>](../../app-domains/gac.md)
