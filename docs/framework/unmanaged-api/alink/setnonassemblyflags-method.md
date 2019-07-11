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
ms.openlocfilehash: 27ad89f1910bc7bb08a23c9fdb0d50828fb8b5e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741433"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="0277f-102">SetNonAssemblyFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="0277f-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="0277f-103">Nastaví příznaky, které nejsou specifické pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="0277f-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0277f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0277f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0277f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0277f-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="0277f-106">Příznaky ALink.</span><span class="sxs-lookup"><span data-stu-id="0277f-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0277f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0277f-107">Return Value</span></span>  
 <span data-ttu-id="0277f-108">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="0277f-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0277f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0277f-109">Requirements</span></span>  
 <span data-ttu-id="0277f-110">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="0277f-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0277f-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0277f-111">See also</span></span>

- [<span data-ttu-id="0277f-112">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0277f-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="0277f-113">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0277f-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="0277f-114">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="0277f-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
