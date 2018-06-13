---
title: CloseAssembly – metoda
ms.date: 03/30/2017
api_name:
- IALink.CloseAssembly
- CloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseAssembly
helpviewer_keywords:
- CloseAssembly method
ms.assetid: f66a43bc-a5c5-4190-acbe-63fd27640634
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 68698aab0fd0872c6e6f67e4ec531ab0226e784f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401950"
---
# <a name="closeassembly-method"></a><span data-ttu-id="a0c3b-102">CloseAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="a0c3b-102">CloseAssembly Method</span></span>
<span data-ttu-id="a0c3b-103">Dokončí operace sestavení.</span><span class="sxs-lookup"><span data-stu-id="a0c3b-103">Finalizes assembly operations.</span></span> <span data-ttu-id="a0c3b-104">Tuto metodu volejte před zahájením nové sestavení nebo nevázaný modulu.</span><span class="sxs-lookup"><span data-stu-id="a0c3b-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0c3b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0c3b-105">Syntax</span></span>  
  
```  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0c3b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0c3b-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="a0c3b-107">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="a0c3b-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0c3b-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a0c3b-108">Return Value</span></span>  
 <span data-ttu-id="a0c3b-109">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="a0c3b-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0c3b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a0c3b-110">Requirements</span></span>  
 <span data-ttu-id="a0c3b-111">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="a0c3b-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0c3b-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0c3b-112">See Also</span></span>  
 [<span data-ttu-id="a0c3b-113">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0c3b-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="a0c3b-114">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0c3b-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="a0c3b-115">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="a0c3b-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
