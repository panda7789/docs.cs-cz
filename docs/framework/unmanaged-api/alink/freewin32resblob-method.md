---
title: FreeWin32ResBlob – metoda
ms.date: 03/30/2017
api_name:
- IALink.FreeWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- FreeWin32ResBlob
helpviewer_keywords:
- FreeWin32ResBlob method
ms.assetid: d941102b-2679-4c49-b15e-c0fc9c53e11f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 196a57b3e919ea4ccbc0b91e5b6f281ad3c30b62
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118154"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="2ebf6-102">FreeWin32ResBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="2ebf6-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="2ebf6-103">Uvolní objekt blob prostředků Win32 a související prostředky.</span><span class="sxs-lookup"><span data-stu-id="2ebf6-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ebf6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ebf6-104">Syntax</span></span>  
  
```  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ebf6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ebf6-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="2ebf6-106">Objekt blob prostředek uvolnit.</span><span class="sxs-lookup"><span data-stu-id="2ebf6-106">The resource blob to be released.</span></span> <span data-ttu-id="2ebf6-107">Tato metoda přiřadí ukazatel objektu blob na hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="2ebf6-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ebf6-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2ebf6-108">Return Value</span></span>  
 <span data-ttu-id="2ebf6-109">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="2ebf6-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ebf6-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2ebf6-110">Requirements</span></span>  
 <span data-ttu-id="2ebf6-111">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="2ebf6-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ebf6-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ebf6-112">See also</span></span>

- [<span data-ttu-id="2ebf6-113">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2ebf6-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="2ebf6-114">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2ebf6-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="2ebf6-115">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="2ebf6-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
