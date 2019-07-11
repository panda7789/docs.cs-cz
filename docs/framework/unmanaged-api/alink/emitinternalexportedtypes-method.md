---
title: EmitInternalExportedTypes – metoda
ms.date: 03/30/2017
api_name:
- EmitInternalExportedTypes
- IALink2.EmitInternalExportedTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitInternalExportedTypes
helpviewer_keywords:
- EmitInternalExportedTypes method
ms.assetid: 28c8b00d-2c14-40b4-aed5-a1db0e2428eb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15174480c4345f2514572701a5525f0f192ad120
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742099"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="abae2-102">EmitInternalExportedTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="abae2-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="abae2-103">Vysílá typy do sestavení.</span><span class="sxs-lookup"><span data-stu-id="abae2-103">Emits types added to the assembly.</span></span> <span data-ttu-id="abae2-104">Volejte tuto metodu po označuje, že byly přidány vnitřní typy.</span><span class="sxs-lookup"><span data-stu-id="abae2-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abae2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abae2-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="abae2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="abae2-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="abae2-107">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="abae2-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="abae2-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="abae2-108">Return Value</span></span>  
 <span data-ttu-id="abae2-109">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="abae2-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abae2-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="abae2-110">Requirements</span></span>  
 <span data-ttu-id="abae2-111">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="abae2-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abae2-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="abae2-112">See also</span></span>

- [<span data-ttu-id="abae2-113">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="abae2-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="abae2-114">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="abae2-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="abae2-115">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="abae2-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
