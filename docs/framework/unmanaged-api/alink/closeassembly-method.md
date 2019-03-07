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
ms.openlocfilehash: c89fd080e61db78ed21c03c2aa63c97337c09585
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497545"
---
# <a name="closeassembly-method"></a><span data-ttu-id="b28e9-102">CloseAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="b28e9-102">CloseAssembly Method</span></span>
<span data-ttu-id="b28e9-103">Dokončí operace sestavení.</span><span class="sxs-lookup"><span data-stu-id="b28e9-103">Finalizes assembly operations.</span></span> <span data-ttu-id="b28e9-104">Tuto metodu volejte před zahájením nové sestavení nebo nevázaného modulu.</span><span class="sxs-lookup"><span data-stu-id="b28e9-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b28e9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b28e9-105">Syntax</span></span>  
  
```  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="b28e9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b28e9-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b28e9-107">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="b28e9-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b28e9-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b28e9-108">Return Value</span></span>  
 <span data-ttu-id="b28e9-109">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="b28e9-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b28e9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b28e9-110">Requirements</span></span>  
 <span data-ttu-id="b28e9-111">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="b28e9-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b28e9-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b28e9-112">See also</span></span>
- [<span data-ttu-id="b28e9-113">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b28e9-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="b28e9-114">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b28e9-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="b28e9-115">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="b28e9-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
