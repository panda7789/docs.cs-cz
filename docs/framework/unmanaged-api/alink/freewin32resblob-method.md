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
ms.openlocfilehash: ea0fbceb1e778a2f26e0625a337b803f417b59eb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777244"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="aa5b8-102">FreeWin32ResBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="aa5b8-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="aa5b8-103">Uvolňuje objekt BLOB prostředku Win32 a přidružené prostředky.</span><span class="sxs-lookup"><span data-stu-id="aa5b8-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa5b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa5b8-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa5b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa5b8-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="aa5b8-106">Objekt BLOB prostředku, který se má uvolnit</span><span class="sxs-lookup"><span data-stu-id="aa5b8-106">The resource blob to be released.</span></span> <span data-ttu-id="aa5b8-107">Tato metoda přiřadí ukazatel objektu BLOB k hodnotě NULL.</span><span class="sxs-lookup"><span data-stu-id="aa5b8-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa5b8-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aa5b8-108">Return Value</span></span>  
 <span data-ttu-id="aa5b8-109">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="aa5b8-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa5b8-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aa5b8-110">Requirements</span></span>  
 <span data-ttu-id="aa5b8-111">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="aa5b8-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa5b8-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa5b8-112">See also</span></span>

- [<span data-ttu-id="aa5b8-113">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa5b8-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="aa5b8-114">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa5b8-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="aa5b8-115">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="aa5b8-115">ALink API</span></span>](index.md)
