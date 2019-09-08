---
title: PreCloseAssembly – metoda
ms.date: 03/30/2017
api_name:
- IALink.PreCloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- PreCloseAssembly
helpviewer_keywords:
- PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4cf862ae3676b85a7fc3f09a4f5794e01284737
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787233"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="73183-102">PreCloseAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="73183-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="73183-103">Zavře soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="73183-103">Closes the assembly file.</span></span> <span data-ttu-id="73183-104">Tuto metodu zavolejte po zavření všech ostatních souborů, ale před zavřením souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="73183-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="73183-105">Nevolejte tuto metodu pro nevázané moduly.</span><span class="sxs-lookup"><span data-stu-id="73183-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73183-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73183-106">Syntax</span></span>  
  
```cpp  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="73183-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="73183-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="73183-108">ID sestavení</span><span class="sxs-lookup"><span data-stu-id="73183-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73183-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="73183-109">Return Value</span></span>  
 <span data-ttu-id="73183-110">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="73183-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73183-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73183-111">Requirements</span></span>  
 <span data-ttu-id="73183-112">Vyžaduje ALink. h.</span><span class="sxs-lookup"><span data-stu-id="73183-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73183-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73183-113">See also</span></span>

- [<span data-ttu-id="73183-114">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73183-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="73183-115">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73183-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="73183-116">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="73183-116">ALink API</span></span>](index.md)
