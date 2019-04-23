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
ms.openlocfilehash: aab42e939651d75b1933962d72ba8bec1090f52d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184506"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="71d72-102">PreCloseAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="71d72-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="71d72-103">Zavře soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="71d72-103">Closes the assembly file.</span></span> <span data-ttu-id="71d72-104">Tuto metodu volejte, ukončete všechny ostatní soubory, ale před zavřením souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="71d72-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="71d72-105">Nevolejte tuto metodu pro nevázaný moduly.</span><span class="sxs-lookup"><span data-stu-id="71d72-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71d72-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71d72-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="71d72-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="71d72-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="71d72-108">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="71d72-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71d72-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="71d72-109">Return Value</span></span>  
 <span data-ttu-id="71d72-110">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="71d72-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71d72-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="71d72-111">Requirements</span></span>  
 <span data-ttu-id="71d72-112">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="71d72-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71d72-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71d72-113">See also</span></span>

- [<span data-ttu-id="71d72-114">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="71d72-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="71d72-115">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="71d72-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="71d72-116">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="71d72-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
