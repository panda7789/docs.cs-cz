---
title: SetNonAssemblyFlags – metoda
ms.date: 03/30/2017
api_name:
- IALink.SetNonAssemblyFlags
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetNonAssemblyFlags
helpviewer_keywords:
- SetNonAssemblyFlags method
ms.assetid: f8ba6fc8-f5aa-4066-ac96-56332758f5ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 78a7dab69e716e1662a277a69c008474d97f9bc4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619646"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="d7879-102">SetNonAssemblyFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="d7879-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="d7879-103">Nastaví příznaky, které nejsou specifické pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7879-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7879-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7879-104">Syntax</span></span>  
  
```  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7879-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7879-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="d7879-106">Příznaky ALink.</span><span class="sxs-lookup"><span data-stu-id="d7879-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7879-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d7879-107">Return Value</span></span>  
 <span data-ttu-id="d7879-108">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="d7879-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7879-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7879-109">Requirements</span></span>  
 <span data-ttu-id="d7879-110">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="d7879-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7879-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7879-111">See also</span></span>
- [<span data-ttu-id="d7879-112">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7879-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="d7879-113">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7879-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="d7879-114">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="d7879-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
