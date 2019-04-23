---
title: EmitAssembly – metoda
ms.date: 03/30/2017
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssembly
helpviewer_keywords:
- EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf7b54ab7a2318e8194bf39dbe41b864633ddb43
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212905"
---
# <a name="emitassembly-method"></a><span data-ttu-id="01453-102">EmitAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="01453-102">EmitAssembly Method</span></span>
<span data-ttu-id="01453-103">Vytvoří sestavení.</span><span class="sxs-lookup"><span data-stu-id="01453-103">Creates the assembly.</span></span> <span data-ttu-id="01453-104">Volejte tuto metodu po všechny ostatní soubory zavřou, s výjimkou souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="01453-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="01453-105">Nevolejte tuto metodu při vytváření nevázaného moduly.</span><span class="sxs-lookup"><span data-stu-id="01453-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01453-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01453-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="01453-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="01453-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="01453-108">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="01453-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01453-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="01453-109">Return Value</span></span>  
 <span data-ttu-id="01453-110">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="01453-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01453-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01453-111">Requirements</span></span>  
 <span data-ttu-id="01453-112">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="01453-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01453-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01453-113">See also</span></span>

- [<span data-ttu-id="01453-114">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01453-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="01453-115">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01453-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="01453-116">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="01453-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
