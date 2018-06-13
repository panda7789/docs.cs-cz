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
ms.openlocfilehash: 1cd1c077a8f2a5fe3b2b46c2e1da2e92b5a797a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402054"
---
# <a name="emitassembly-method"></a><span data-ttu-id="61dcf-102">EmitAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="61dcf-102">EmitAssembly Method</span></span>
<span data-ttu-id="61dcf-103">Vytvoří sestavení.</span><span class="sxs-lookup"><span data-stu-id="61dcf-103">Creates the assembly.</span></span> <span data-ttu-id="61dcf-104">Volejte tuto metodu po zavřeny všechny ostatní soubory s výjimkou souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="61dcf-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="61dcf-105">Tato metoda není volána při vytváření nevázaný moduly.</span><span class="sxs-lookup"><span data-stu-id="61dcf-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61dcf-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61dcf-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61dcf-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="61dcf-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="61dcf-108">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="61dcf-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61dcf-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="61dcf-109">Return Value</span></span>  
 <span data-ttu-id="61dcf-110">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="61dcf-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61dcf-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="61dcf-111">Requirements</span></span>  
 <span data-ttu-id="61dcf-112">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="61dcf-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61dcf-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="61dcf-113">See Also</span></span>  
 [<span data-ttu-id="61dcf-114">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61dcf-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="61dcf-115">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61dcf-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="61dcf-116">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="61dcf-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
