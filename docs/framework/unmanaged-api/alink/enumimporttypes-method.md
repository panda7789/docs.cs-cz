---
title: "EnumImportTypes – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 08644816d3fa11ade5a8ebee1573e8f66d526101
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="f6db5-102">EnumImportTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="f6db5-102">EnumImportTypes Method</span></span>
<span data-ttu-id="f6db5-103">Vytvoří výčet jednotlivých typů v každém oboru.</span><span class="sxs-lookup"><span data-stu-id="f6db5-103">Enumerates each type in each scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6db5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6db5-104">Syntax</span></span>  
  
```  
HRESULT EnumImportTypes(  
    HALINKENUM   hEnum,  
    DWORD        dwMax,  
    mdTypeDef    aTypeDefs[],  
    DWORD*       pdwCount  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6db5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6db5-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="f6db5-106">Obslužná rutina pro enumerátor.</span><span class="sxs-lookup"><span data-stu-id="f6db5-106">Handle for enumerator.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="f6db5-107">Maximální počet typů, který chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="f6db5-107">Maximum number of types to retrieve.</span></span>  
  
 `aTypeDefs`  
 <span data-ttu-id="f6db5-108">Recieves zadejte tokeny nepřesahující `dwMax`.</span><span class="sxs-lookup"><span data-stu-id="f6db5-108">Recieves type tokens, not to exceed `dwMax`.</span></span>  
  
 `pdwCount`  
 <span data-ttu-id="f6db5-109">Získá skutečný počet typu v `aTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="f6db5-109">Receives actual number of type in `aTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6db5-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f6db5-110">Return Value</span></span>  
 <span data-ttu-id="f6db5-111">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="f6db5-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6db5-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f6db5-112">Requirements</span></span>  
 <span data-ttu-id="f6db5-113">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="f6db5-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6db5-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6db5-114">See Also</span></span>  
 [<span data-ttu-id="f6db5-115">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6db5-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="f6db5-116">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6db5-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="f6db5-117">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="f6db5-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
