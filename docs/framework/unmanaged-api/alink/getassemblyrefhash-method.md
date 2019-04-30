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
ms.openlocfilehash: 6fa8d42f9e849db6a02f6c62b37e04cf5dee016e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789854"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="3e37a-102">GetAssemblyRefHash – metoda</span><span class="sxs-lookup"><span data-stu-id="3e37a-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="3e37a-103">Načte objekt blob algoritmu hash pro dané sestavení.</span><span class="sxs-lookup"><span data-stu-id="3e37a-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e37a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e37a-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e37a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e37a-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="3e37a-106">ID sestavení, na který bude odkazovat-the-hash.</span><span class="sxs-lookup"><span data-stu-id="3e37a-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="3e37a-107">Získá výsledný objekt blob algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="3e37a-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="3e37a-108">Přijímá velikost v bajtech, objekt blob algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="3e37a-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e37a-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3e37a-109">Return Value</span></span>  
 <span data-ttu-id="3e37a-110">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="3e37a-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e37a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e37a-111">Requirements</span></span>  
 <span data-ttu-id="3e37a-112">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="3e37a-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e37a-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e37a-113">See also</span></span>

- [<span data-ttu-id="3e37a-114">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e37a-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="3e37a-115">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e37a-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="3e37a-116">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="3e37a-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
