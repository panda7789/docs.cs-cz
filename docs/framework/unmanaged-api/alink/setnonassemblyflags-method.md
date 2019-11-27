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
ms.openlocfilehash: 2dcb363a2a84b3c2e0438e45663b96d9a0f83f61
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445550"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="828c2-102">SetNonAssemblyFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="828c2-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="828c2-103">Nastaví příznaky, které nejsou specifické pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="828c2-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="828c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="828c2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="828c2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="828c2-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="828c2-106">Příznaky ALink</span><span class="sxs-lookup"><span data-stu-id="828c2-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="828c2-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="828c2-107">Return Value</span></span>  
 <span data-ttu-id="828c2-108">Vrátí S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="828c2-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="828c2-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="828c2-109">Requirements</span></span>  
 <span data-ttu-id="828c2-110">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="828c2-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="828c2-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="828c2-111">See also</span></span>

- [<span data-ttu-id="828c2-112">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="828c2-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="828c2-113">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="828c2-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="828c2-114">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="828c2-114">ALink API</span></span>](index.md)
