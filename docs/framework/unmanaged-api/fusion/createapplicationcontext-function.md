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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25364330dafdf858c4b41e9a05731c37e97fbb57
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795429"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="bf74b-102">CreateApplicationContext – funkce</span><span class="sxs-lookup"><span data-stu-id="bf74b-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="bf74b-103">Tato funkce podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="bf74b-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf74b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf74b-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf74b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf74b-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="bf74b-106">pro Ukazatel na popisný název.</span><span class="sxs-lookup"><span data-stu-id="bf74b-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="bf74b-107">mimo Ukazatel na kontext aplikace.</span><span class="sxs-lookup"><span data-stu-id="bf74b-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf74b-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bf74b-108">Requirements</span></span>  
 <span data-ttu-id="bf74b-109">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf74b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf74b-110">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="bf74b-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="bf74b-111">**Knihovna** Zahrnuto jako prostředek v Fusion. dll</span><span class="sxs-lookup"><span data-stu-id="bf74b-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="bf74b-112">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf74b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf74b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf74b-113">See also</span></span>

- [<span data-ttu-id="bf74b-114">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf74b-114">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="bf74b-115">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="bf74b-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="bf74b-116">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="bf74b-116">Global Assembly Cache</span></span>](../../app-domains/gac.md)
