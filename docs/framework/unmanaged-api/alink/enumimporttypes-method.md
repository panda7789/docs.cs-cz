---
title: "EnumImportTypes – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location: alink.dll
api_type: COM
f1_keywords: EnumImportTypes
helpviewer_keywords: EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: df6efbc86ff958cb8a715c81f86ea1112629fe67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="b7949-102">EnumImportTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="b7949-102">EnumImportTypes Method</span></span>
<span data-ttu-id="b7949-103">Vytvoří výčet jednotlivých typů v každém oboru.</span><span class="sxs-lookup"><span data-stu-id="b7949-103">Enumerates each type in each scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7949-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7949-104">Syntax</span></span>  
  
```  
HRESULT EnumImportTypes(  
    HALINKENUM   hEnum,  
    DWORD        dwMax,  
    mdTypeDef    aTypeDefs[],  
    DWORD*       pdwCount  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7949-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7949-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="b7949-106">Obslužná rutina pro enumerátor.</span><span class="sxs-lookup"><span data-stu-id="b7949-106">Handle for enumerator.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="b7949-107">Maximální počet typů, který chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="b7949-107">Maximum number of types to retrieve.</span></span>  
  
 `aTypeDefs`  
 <span data-ttu-id="b7949-108">Recieves zadejte tokeny nepřesahující `dwMax`.</span><span class="sxs-lookup"><span data-stu-id="b7949-108">Recieves type tokens, not to exceed `dwMax`.</span></span>  
  
 `pdwCount`  
 <span data-ttu-id="b7949-109">Získá skutečný počet typu v `aTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="b7949-109">Receives actual number of type in `aTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7949-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b7949-110">Return Value</span></span>  
 <span data-ttu-id="b7949-111">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="b7949-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7949-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7949-112">Requirements</span></span>  
 <span data-ttu-id="b7949-113">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="b7949-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7949-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7949-114">See Also</span></span>  
 [<span data-ttu-id="b7949-115">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7949-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="b7949-116">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7949-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="b7949-117">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="b7949-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
