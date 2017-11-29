---
title: "SetNonAssemblyFlags – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.SetNonAssemblyFlags
api_location: alink.dll
api_type: COM
f1_keywords: SetNonAssemblyFlags
helpviewer_keywords: SetNonAssemblyFlags method
ms.assetid: f8ba6fc8-f5aa-4066-ac96-56332758f5ec
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c5f8761259e89b4befd0eeaf893ffbe5d4142350
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="a0d80-102">SetNonAssemblyFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="a0d80-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="a0d80-103">Nastaví příznaky, které nejsou specifické pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="a0d80-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0d80-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0d80-104">Syntax</span></span>  
  
```  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0d80-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0d80-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="a0d80-106">Příznaky ALink.</span><span class="sxs-lookup"><span data-stu-id="a0d80-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0d80-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a0d80-107">Return Value</span></span>  
 <span data-ttu-id="a0d80-108">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="a0d80-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0d80-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a0d80-109">Requirements</span></span>  
 <span data-ttu-id="a0d80-110">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="a0d80-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0d80-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0d80-111">See Also</span></span>  
 [<span data-ttu-id="a0d80-112">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0d80-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="a0d80-113">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0d80-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="a0d80-114">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="a0d80-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
