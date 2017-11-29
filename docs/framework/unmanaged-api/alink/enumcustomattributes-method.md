---
title: "EnumCustomAttributes – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EnumCustomAttributes
- IALink.EnumCustomAttributes
api_location: alink.dll
api_type: COM
f1_keywords: EnumCustomAttributes
helpviewer_keywords: EnumCustomAttributes method
ms.assetid: 08dff60c-f01b-4050-8865-ea3f95361c9f
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: febaba5155753e9d60a3708582f4f58bd7861ec7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="d5fa0-102">EnumCustomAttributes – metoda</span><span class="sxs-lookup"><span data-stu-id="d5fa0-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="d5fa0-103">Načte vlastní atributy úrovně sestavení.</span><span class="sxs-lookup"><span data-stu-id="d5fa0-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5fa0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5fa0-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5fa0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5fa0-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="d5fa0-106">Popisovač výčtu.</span><span class="sxs-lookup"><span data-stu-id="d5fa0-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="d5fa0-107">Typ atributů, které chcete vytvořit její výčet.</span><span class="sxs-lookup"><span data-stu-id="d5fa0-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="d5fa0-108">Použití `mdTokenNill` pro všechny atributy.</span><span class="sxs-lookup"><span data-stu-id="d5fa0-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="d5fa0-109">Přijímá tokeny vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="d5fa0-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d5fa0-110">Určuje velikost `rCustomValues` pole.</span><span class="sxs-lookup"><span data-stu-id="d5fa0-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="d5fa0-111">Volitelně obdrží počet hodnoty tokenu.</span><span class="sxs-lookup"><span data-stu-id="d5fa0-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5fa0-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d5fa0-112">Return Value</span></span>  
 <span data-ttu-id="d5fa0-113">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="d5fa0-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5fa0-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5fa0-114">Requirements</span></span>  
 <span data-ttu-id="d5fa0-115">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="d5fa0-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5fa0-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5fa0-116">See Also</span></span>  
 [<span data-ttu-id="d5fa0-117">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5fa0-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="d5fa0-118">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5fa0-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="d5fa0-119">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="d5fa0-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
