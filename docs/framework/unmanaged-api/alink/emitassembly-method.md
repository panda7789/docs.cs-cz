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
ms.openlocfilehash: 6bbe5db75ded15f32a6ff3564e1116d40a745a65
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446531"
---
# <a name="emitassembly-method"></a><span data-ttu-id="8ffd4-102">EmitAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="8ffd4-102">EmitAssembly Method</span></span>
<span data-ttu-id="8ffd4-103">Vytvoří sestavení.</span><span class="sxs-lookup"><span data-stu-id="8ffd4-103">Creates the assembly.</span></span> <span data-ttu-id="8ffd4-104">Tuto metodu volejte po zavření všech ostatních souborů s výjimkou souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="8ffd4-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="8ffd4-105">Nevolejte tuto metodu při vytváření nevázaných modulů.</span><span class="sxs-lookup"><span data-stu-id="8ffd4-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ffd4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ffd4-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ffd4-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ffd4-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8ffd4-108">ID sestavení</span><span class="sxs-lookup"><span data-stu-id="8ffd4-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ffd4-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8ffd4-109">Return Value</span></span>  
 <span data-ttu-id="8ffd4-110">Vrátí S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="8ffd4-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ffd4-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ffd4-111">Requirements</span></span>  
 <span data-ttu-id="8ffd4-112">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="8ffd4-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ffd4-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ffd4-113">See also</span></span>

- [<span data-ttu-id="8ffd4-114">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ffd4-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="8ffd4-115">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ffd4-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="8ffd4-116">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="8ffd4-116">ALink API</span></span>](index.md)
