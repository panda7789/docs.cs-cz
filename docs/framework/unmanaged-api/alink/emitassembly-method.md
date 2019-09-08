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
ms.openlocfilehash: a2adf53d1e29fda077cdcf7b79891f6271993109
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787579"
---
# <a name="emitassembly-method"></a><span data-ttu-id="e2f10-102">EmitAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="e2f10-102">EmitAssembly Method</span></span>
<span data-ttu-id="e2f10-103">Vytvoří sestavení.</span><span class="sxs-lookup"><span data-stu-id="e2f10-103">Creates the assembly.</span></span> <span data-ttu-id="e2f10-104">Tuto metodu volejte po zavření všech ostatních souborů s výjimkou souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="e2f10-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="e2f10-105">Nevolejte tuto metodu při vytváření nevázaných modulů.</span><span class="sxs-lookup"><span data-stu-id="e2f10-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2f10-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2f10-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2f10-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2f10-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e2f10-108">ID sestavení</span><span class="sxs-lookup"><span data-stu-id="e2f10-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2f10-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e2f10-109">Return Value</span></span>  
 <span data-ttu-id="e2f10-110">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="e2f10-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2f10-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2f10-111">Requirements</span></span>  
 <span data-ttu-id="e2f10-112">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="e2f10-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2f10-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2f10-113">See also</span></span>

- [<span data-ttu-id="e2f10-114">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2f10-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="e2f10-115">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2f10-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="e2f10-116">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="e2f10-116">ALink API</span></span>](index.md)
