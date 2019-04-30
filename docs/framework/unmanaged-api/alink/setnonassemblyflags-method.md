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
ms.openlocfilehash: c7716db814e86258c4cb81047b39142f33798782
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949021"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="01f07-102">SetNonAssemblyFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="01f07-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="01f07-103">Nastaví příznaky, které nejsou specifické pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="01f07-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01f07-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01f07-104">Syntax</span></span>  
  
```  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="01f07-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01f07-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="01f07-106">Příznaky ALink.</span><span class="sxs-lookup"><span data-stu-id="01f07-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01f07-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="01f07-107">Return Value</span></span>  
 <span data-ttu-id="01f07-108">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="01f07-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01f07-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01f07-109">Requirements</span></span>  
 <span data-ttu-id="01f07-110">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="01f07-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01f07-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01f07-111">See also</span></span>

- [<span data-ttu-id="01f07-112">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01f07-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="01f07-113">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01f07-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="01f07-114">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="01f07-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
