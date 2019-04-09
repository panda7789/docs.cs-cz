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
ms.openlocfilehash: d98829b29100824e5d606e23aaf287c9f6e81d69
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170960"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="d7e0b-102">CreateApplicationContext – funkce</span><span class="sxs-lookup"><span data-stu-id="d7e0b-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="d7e0b-103">Tato funkce podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="d7e0b-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7e0b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7e0b-104">Syntax</span></span>  
  
```  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7e0b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7e0b-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="d7e0b-106">[in] Ukazatel na popisný název.</span><span class="sxs-lookup"><span data-stu-id="d7e0b-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="d7e0b-107">[out] Ukazatel na objekt context aplikace.</span><span class="sxs-lookup"><span data-stu-id="d7e0b-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7e0b-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7e0b-108">Requirements</span></span>  
 <span data-ttu-id="d7e0b-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7e0b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7e0b-110">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d7e0b-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d7e0b-111">**Knihovna:** Zahrnuté jako prostředek v soubor Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="d7e0b-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 **<span data-ttu-id="d7e0b-112">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d7e0b-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d7e0b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7e0b-113">See also</span></span>

- [<span data-ttu-id="d7e0b-114">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7e0b-114">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [<span data-ttu-id="d7e0b-115">Fúze globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="d7e0b-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [<span data-ttu-id="d7e0b-116">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="d7e0b-116">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
