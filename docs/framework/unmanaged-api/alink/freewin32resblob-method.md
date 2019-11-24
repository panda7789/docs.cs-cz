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
ms.openlocfilehash: 2b1addc752c7238116e072c6e957d2b277ceb1e3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449399"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="b9f39-102">FreeWin32ResBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="b9f39-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="b9f39-103">Releases the Win32 resource blob and associated resources.</span><span class="sxs-lookup"><span data-stu-id="b9f39-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9f39-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9f39-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9f39-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b9f39-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="b9f39-106">The resource blob to be released.</span><span class="sxs-lookup"><span data-stu-id="b9f39-106">The resource blob to be released.</span></span> <span data-ttu-id="b9f39-107">This method assigns the blob pointer to NULL.</span><span class="sxs-lookup"><span data-stu-id="b9f39-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9f39-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b9f39-108">Return Value</span></span>  
 <span data-ttu-id="b9f39-109">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="b9f39-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9f39-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9f39-110">Requirements</span></span>  
 <span data-ttu-id="b9f39-111">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="b9f39-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9f39-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9f39-112">See also</span></span>

- [<span data-ttu-id="b9f39-113">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9f39-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="b9f39-114">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9f39-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="b9f39-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="b9f39-115">ALink API</span></span>](index.md)
