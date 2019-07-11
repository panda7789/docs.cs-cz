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
ms.openlocfilehash: b0e6250987997b8d1c833b7b33a985900510fb03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742134"
---
# <a name="emitassembly-method"></a><span data-ttu-id="799c7-102">EmitAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="799c7-102">EmitAssembly Method</span></span>
<span data-ttu-id="799c7-103">Vytvoří sestavení.</span><span class="sxs-lookup"><span data-stu-id="799c7-103">Creates the assembly.</span></span> <span data-ttu-id="799c7-104">Volejte tuto metodu po všechny ostatní soubory zavřou, s výjimkou souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="799c7-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="799c7-105">Nevolejte tuto metodu při vytváření nevázaného moduly.</span><span class="sxs-lookup"><span data-stu-id="799c7-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="799c7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="799c7-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="799c7-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="799c7-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="799c7-108">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="799c7-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="799c7-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="799c7-109">Return Value</span></span>  
 <span data-ttu-id="799c7-110">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="799c7-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="799c7-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="799c7-111">Requirements</span></span>  
 <span data-ttu-id="799c7-112">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="799c7-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="799c7-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="799c7-113">See also</span></span>

- [<span data-ttu-id="799c7-114">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="799c7-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="799c7-115">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="799c7-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="799c7-116">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="799c7-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
