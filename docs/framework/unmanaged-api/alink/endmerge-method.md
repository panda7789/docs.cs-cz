---
title: EndMerge – metoda
ms.date: 03/30/2017
api_name:
- IALink.EndMerge
- EndMerge
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EndMerge
helpviewer_keywords:
- EndMerge method
ms.assetid: 1d03bb15-a2c8-4a04-8fc6-b126c89c3778
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 020cc56126249b27a52387e6efa3aa10c83d9126
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789984"
---
# <a name="endmerge-method"></a><span data-ttu-id="da5e7-102">EndMerge – metoda</span><span class="sxs-lookup"><span data-stu-id="da5e7-102">EndMerge Method</span></span>
<span data-ttu-id="da5e7-103">Označuje, že všechny vlastní atributy byly sloučeny do rozsahu vygeneruje.</span><span class="sxs-lookup"><span data-stu-id="da5e7-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da5e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da5e7-104">Syntax</span></span>  
  
```  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="da5e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da5e7-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="da5e7-106">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="da5e7-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da5e7-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="da5e7-107">Return Value</span></span>  
 <span data-ttu-id="da5e7-108">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="da5e7-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da5e7-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da5e7-109">Requirements</span></span>  
 <span data-ttu-id="da5e7-110">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="da5e7-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da5e7-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da5e7-111">See also</span></span>

- [<span data-ttu-id="da5e7-112">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da5e7-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="da5e7-113">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da5e7-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="da5e7-114">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="da5e7-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
