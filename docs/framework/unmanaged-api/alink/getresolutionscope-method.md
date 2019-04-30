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
ms.openlocfilehash: 6c6d298c84b801b87832c56026b05f647cb5a9dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789828"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="7eee0-102">GetResolutionScope – metoda</span><span class="sxs-lookup"><span data-stu-id="7eee0-102">GetResolutionScope Method</span></span>
<span data-ttu-id="7eee0-103">Načte oboru daného typu.</span><span class="sxs-lookup"><span data-stu-id="7eee0-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eee0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7eee0-104">Syntax</span></span>  
  
```  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="7eee0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7eee0-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="7eee0-106">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="7eee0-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="7eee0-107">Soubor, který je potřeba zkontrolovat odkaz.</span><span class="sxs-lookup"><span data-stu-id="7eee0-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="7eee0-108">Token souboru tento typ je definován v, obvykle získáte pomocí [importfile – metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="7eee0-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="7eee0-109">Přijímá sestavení nebo odkaz na modul.</span><span class="sxs-lookup"><span data-stu-id="7eee0-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7eee0-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7eee0-110">Return Value</span></span>  
 <span data-ttu-id="7eee0-111">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="7eee0-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7eee0-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7eee0-112">Requirements</span></span>  
 <span data-ttu-id="7eee0-113">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="7eee0-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eee0-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7eee0-114">See also</span></span>

- [<span data-ttu-id="7eee0-115">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7eee0-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="7eee0-116">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7eee0-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="7eee0-117">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="7eee0-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
