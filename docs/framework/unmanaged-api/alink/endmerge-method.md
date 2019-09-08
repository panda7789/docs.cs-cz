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
ms.openlocfilehash: 88f594117fffedb6acafef26a9e834dd951ea5bb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787525"
---
# <a name="endmerge-method"></a><span data-ttu-id="4788c-102">EndMerge – metoda</span><span class="sxs-lookup"><span data-stu-id="4788c-102">EndMerge Method</span></span>
<span data-ttu-id="4788c-103">Označuje, že všechny vlastní atributy byly sloučeny do oboru generování.</span><span class="sxs-lookup"><span data-stu-id="4788c-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4788c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4788c-104">Syntax</span></span>  
  
```cpp  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="4788c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4788c-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="4788c-106">ID sestavení</span><span class="sxs-lookup"><span data-stu-id="4788c-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4788c-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4788c-107">Return Value</span></span>  
 <span data-ttu-id="4788c-108">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="4788c-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4788c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4788c-109">Requirements</span></span>  
 <span data-ttu-id="4788c-110">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="4788c-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4788c-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4788c-111">See also</span></span>

- [<span data-ttu-id="4788c-112">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4788c-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="4788c-113">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4788c-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="4788c-114">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="4788c-114">ALink API</span></span>](index.md)
