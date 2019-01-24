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
ms.openlocfilehash: f8d230d5396c5a088fa76a7ca145b4a22d1e1d07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543354"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="d1ed7-102">GetResolutionScope – metoda</span><span class="sxs-lookup"><span data-stu-id="d1ed7-102">GetResolutionScope Method</span></span>
<span data-ttu-id="d1ed7-103">Načte oboru daného typu.</span><span class="sxs-lookup"><span data-stu-id="d1ed7-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1ed7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1ed7-104">Syntax</span></span>  
  
```  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1ed7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1ed7-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d1ed7-106">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="d1ed7-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="d1ed7-107">Soubor, který je potřeba zkontrolovat odkaz.</span><span class="sxs-lookup"><span data-stu-id="d1ed7-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="d1ed7-108">Token souboru tento typ je definován v, obvykle získáte pomocí [importfile – metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="d1ed7-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="d1ed7-109">Přijímá sestavení nebo odkaz na modul.</span><span class="sxs-lookup"><span data-stu-id="d1ed7-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1ed7-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d1ed7-110">Return Value</span></span>  
 <span data-ttu-id="d1ed7-111">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="d1ed7-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1ed7-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d1ed7-112">Requirements</span></span>  
 <span data-ttu-id="d1ed7-113">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="d1ed7-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1ed7-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d1ed7-114">See also</span></span>
- [<span data-ttu-id="d1ed7-115">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1ed7-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="d1ed7-116">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1ed7-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="d1ed7-117">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="d1ed7-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
