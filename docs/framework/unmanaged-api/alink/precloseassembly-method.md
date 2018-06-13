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
ms.openlocfilehash: 82421fa83a6f0d24492d70f961e731b679c25728
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400715"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="0c568-102">PreCloseAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="0c568-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="0c568-103">Zavře souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="0c568-103">Closes the assembly file.</span></span> <span data-ttu-id="0c568-104">Volejte tuto metodu po zavření všechny ostatní soubory, ale před jeho zavřením souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="0c568-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="0c568-105">Nevolejte tuto metodu pro nevázaný moduly.</span><span class="sxs-lookup"><span data-stu-id="0c568-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c568-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c568-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0c568-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c568-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="0c568-108">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="0c568-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c568-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0c568-109">Return Value</span></span>  
 <span data-ttu-id="0c568-110">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="0c568-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c568-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0c568-111">Requirements</span></span>  
 <span data-ttu-id="0c568-112">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="0c568-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c568-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c568-113">See Also</span></span>  
 [<span data-ttu-id="0c568-114">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c568-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="0c568-115">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c568-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="0c568-116">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="0c568-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
