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
ms.openlocfilehash: d124ce5dd38bed7eb439a055ff9e30a75efe5891
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400741"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="92458-102">FreeWin32ResBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="92458-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="92458-103">Uvolní Win32 prostředků blob a přidružených prostředků.</span><span class="sxs-lookup"><span data-stu-id="92458-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92458-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92458-104">Syntax</span></span>  
  
```  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92458-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92458-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="92458-106">Objekt blob prostředků k uvolnění.</span><span class="sxs-lookup"><span data-stu-id="92458-106">The resource blob to be released.</span></span> <span data-ttu-id="92458-107">Tato metoda přiřadí objekt blob ukazatel na hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="92458-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92458-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="92458-108">Return Value</span></span>  
 <span data-ttu-id="92458-109">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="92458-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92458-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="92458-110">Requirements</span></span>  
 <span data-ttu-id="92458-111">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="92458-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92458-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="92458-112">See Also</span></span>  
 [<span data-ttu-id="92458-113">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92458-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="92458-114">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92458-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="92458-115">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="92458-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
