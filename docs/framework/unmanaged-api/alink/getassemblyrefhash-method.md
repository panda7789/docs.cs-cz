---
title: "GetAssemblyRefHash – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.GetAssemblyRefHash
api_location: alink.dll
api_type: COM
f1_keywords: GetAssemblyRefHash
helpviewer_keywords: GetAssemblyRefHash method
ms.assetid: 091a18bd-e901-46f6-b999-74d71c8a7c41
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99ae38025f223d669a428738783676ebc0687554
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="08fd5-102">GetAssemblyRefHash – metoda</span><span class="sxs-lookup"><span data-stu-id="08fd5-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="08fd5-103">Načte hodnotu hash objektu blob pro zadaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="08fd5-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08fd5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08fd5-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08fd5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="08fd5-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="08fd5-106">ID sestavení, ke které se budou vztahovat hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="08fd5-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="08fd5-107">Získá výsledný objekt blob hash.</span><span class="sxs-lookup"><span data-stu-id="08fd5-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="08fd5-108">Obdrží velikost v bajtech hash objektů blob.</span><span class="sxs-lookup"><span data-stu-id="08fd5-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08fd5-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="08fd5-109">Return Value</span></span>  
 <span data-ttu-id="08fd5-110">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="08fd5-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08fd5-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="08fd5-111">Requirements</span></span>  
 <span data-ttu-id="08fd5-112">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="08fd5-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08fd5-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="08fd5-113">See Also</span></span>  
 [<span data-ttu-id="08fd5-114">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="08fd5-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="08fd5-115">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="08fd5-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="08fd5-116">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="08fd5-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
