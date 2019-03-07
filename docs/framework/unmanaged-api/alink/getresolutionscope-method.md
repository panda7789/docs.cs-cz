---
title: GetResolutionScope – metoda
ms.date: 03/30/2017
api_name:
- IALink.GetResolutionScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetResolutionScope
helpviewer_keywords:
- GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bfe06c1300a22757b363236454f4f494dab1978a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486794"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="2cbe1-102">GetResolutionScope – metoda</span><span class="sxs-lookup"><span data-stu-id="2cbe1-102">GetResolutionScope Method</span></span>
<span data-ttu-id="2cbe1-103">Načte oboru daného typu.</span><span class="sxs-lookup"><span data-stu-id="2cbe1-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cbe1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cbe1-104">Syntax</span></span>  
  
```  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cbe1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2cbe1-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="2cbe1-106">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="2cbe1-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="2cbe1-107">Soubor, který je potřeba zkontrolovat odkaz.</span><span class="sxs-lookup"><span data-stu-id="2cbe1-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="2cbe1-108">Token souboru tento typ je definován v, obvykle získáte pomocí [importfile – metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="2cbe1-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="2cbe1-109">Přijímá sestavení nebo odkaz na modul.</span><span class="sxs-lookup"><span data-stu-id="2cbe1-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cbe1-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2cbe1-110">Return Value</span></span>  
 <span data-ttu-id="2cbe1-111">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="2cbe1-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cbe1-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2cbe1-112">Requirements</span></span>  
 <span data-ttu-id="2cbe1-113">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="2cbe1-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cbe1-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2cbe1-114">See also</span></span>
- [<span data-ttu-id="2cbe1-115">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2cbe1-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="2cbe1-116">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2cbe1-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="2cbe1-117">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="2cbe1-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
