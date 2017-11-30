---
title: "PreCloseAssembly – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.PreCloseAssembly
api_location: alink.dll
api_type: COM
f1_keywords: PreCloseAssembly
helpviewer_keywords: PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8d940cbdeddc7030c679fae8c8694bb3542123b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="precloseassembly-method"></a><span data-ttu-id="26dac-102">PreCloseAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="26dac-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="26dac-103">Zavře souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="26dac-103">Closes the assembly file.</span></span> <span data-ttu-id="26dac-104">Volejte tuto metodu po zavření všechny ostatní soubory, ale před jeho zavřením souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="26dac-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="26dac-105">Nevolejte tuto metodu pro nevázaný moduly.</span><span class="sxs-lookup"><span data-stu-id="26dac-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26dac-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26dac-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26dac-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="26dac-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="26dac-108">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="26dac-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26dac-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="26dac-109">Return Value</span></span>  
 <span data-ttu-id="26dac-110">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="26dac-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26dac-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="26dac-111">Requirements</span></span>  
 <span data-ttu-id="26dac-112">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="26dac-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26dac-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="26dac-113">See Also</span></span>  
 [<span data-ttu-id="26dac-114">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="26dac-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="26dac-115">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="26dac-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="26dac-116">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="26dac-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
