---
title: CloseAssembly – metoda
ms.date: 03/30/2017
api_name:
- IALink.CloseAssembly
- CloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseAssembly
helpviewer_keywords:
- CloseAssembly method
ms.assetid: f66a43bc-a5c5-4190-acbe-63fd27640634
topic_type:
- apiref
ms.openlocfilehash: 70dca19075d8c896408ec78f89549b0c539280de
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446576"
---
# <a name="closeassembly-method"></a><span data-ttu-id="a8a8a-102">CloseAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="a8a8a-102">CloseAssembly Method</span></span>
<span data-ttu-id="a8a8a-103">Dokončí operace sestavení.</span><span class="sxs-lookup"><span data-stu-id="a8a8a-103">Finalizes assembly operations.</span></span> <span data-ttu-id="a8a8a-104">Před zahájením nového sestavení nebo nevázaného modulu volejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="a8a8a-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8a8a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8a8a-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8a8a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8a8a-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="a8a8a-107">ID sestavení</span><span class="sxs-lookup"><span data-stu-id="a8a8a-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8a8a-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a8a8a-108">Return Value</span></span>  
 <span data-ttu-id="a8a8a-109">Vrátí S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="a8a8a-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8a8a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a8a8a-110">Requirements</span></span>  
 <span data-ttu-id="a8a8a-111">Vyžaduje ALink. h.</span><span class="sxs-lookup"><span data-stu-id="a8a8a-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8a8a-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8a8a-112">See also</span></span>

- [<span data-ttu-id="a8a8a-113">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8a8a-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="a8a8a-114">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8a8a-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="a8a8a-115">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="a8a8a-115">ALink API</span></span>](index.md)
