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
ms.openlocfilehash: e52984e12f22486212f0a2ec02d452a77242400e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491825"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="96a85-102">FreeWin32ResBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="96a85-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="96a85-103">Uvolní objekt blob prostředků Win32 a související prostředky.</span><span class="sxs-lookup"><span data-stu-id="96a85-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96a85-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96a85-104">Syntax</span></span>  
  
```  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="96a85-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96a85-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="96a85-106">Objekt blob prostředek uvolnit.</span><span class="sxs-lookup"><span data-stu-id="96a85-106">The resource blob to be released.</span></span> <span data-ttu-id="96a85-107">Tato metoda přiřadí ukazatel objektu blob na hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="96a85-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96a85-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="96a85-108">Return Value</span></span>  
 <span data-ttu-id="96a85-109">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="96a85-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96a85-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="96a85-110">Requirements</span></span>  
 <span data-ttu-id="96a85-111">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="96a85-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96a85-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96a85-112">See also</span></span>
- [<span data-ttu-id="96a85-113">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96a85-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="96a85-114">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96a85-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="96a85-115">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="96a85-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
