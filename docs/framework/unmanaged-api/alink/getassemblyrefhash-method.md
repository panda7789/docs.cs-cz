---
title: GetAssemblyRefHash – metoda
ms.date: 03/30/2017
api_name:
- IALink.GetAssemblyRefHash
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetAssemblyRefHash
helpviewer_keywords:
- GetAssemblyRefHash method
ms.assetid: 091a18bd-e901-46f6-b999-74d71c8a7c41
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ccf60d067af356dda1870a2fb1dcca21966f16a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401483"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="072ae-102">GetAssemblyRefHash – metoda</span><span class="sxs-lookup"><span data-stu-id="072ae-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="072ae-103">Načte hodnotu hash objektu blob pro zadaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="072ae-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="072ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="072ae-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="072ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="072ae-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="072ae-106">ID sestavení, ke které se budou vztahovat hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="072ae-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="072ae-107">Získá výsledný objekt blob hash.</span><span class="sxs-lookup"><span data-stu-id="072ae-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="072ae-108">Obdrží velikost v bajtech hash objektů blob.</span><span class="sxs-lookup"><span data-stu-id="072ae-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="072ae-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="072ae-109">Return Value</span></span>  
 <span data-ttu-id="072ae-110">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="072ae-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="072ae-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="072ae-111">Requirements</span></span>  
 <span data-ttu-id="072ae-112">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="072ae-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="072ae-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="072ae-113">See Also</span></span>  
 [<span data-ttu-id="072ae-114">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="072ae-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="072ae-115">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="072ae-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="072ae-116">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="072ae-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
