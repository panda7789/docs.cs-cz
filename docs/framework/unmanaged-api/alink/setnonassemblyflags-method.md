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
ms.openlocfilehash: e8a22e958740b69ba0e09bf062bf4d86075c3ff1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777020"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="44261-102">SetNonAssemblyFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="44261-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="44261-103">Nastaví příznaky, které nejsou specifické pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="44261-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44261-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44261-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="44261-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44261-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="44261-106">Příznaky ALink</span><span class="sxs-lookup"><span data-stu-id="44261-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44261-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="44261-107">Return Value</span></span>  
 <span data-ttu-id="44261-108">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="44261-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44261-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="44261-109">Requirements</span></span>  
 <span data-ttu-id="44261-110">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="44261-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44261-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44261-111">See also</span></span>

- [<span data-ttu-id="44261-112">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44261-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="44261-113">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44261-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="44261-114">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="44261-114">ALink API</span></span>](index.md)
