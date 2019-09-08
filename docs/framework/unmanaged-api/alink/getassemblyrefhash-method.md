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
ms.openlocfilehash: d19eebaa3aa0ebb6f9807f0cf277b7ed6183c148
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777191"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="642ae-102">GetAssemblyRefHash – metoda</span><span class="sxs-lookup"><span data-stu-id="642ae-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="642ae-103">Načte objekt BLOB algoritmu hash pro dané sestavení.</span><span class="sxs-lookup"><span data-stu-id="642ae-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="642ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="642ae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="642ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="642ae-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="642ae-106">ID sestavení, na které bude odkazovat hodnota hash</span><span class="sxs-lookup"><span data-stu-id="642ae-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="642ae-107">Přijímá výsledný objekt BLOB algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="642ae-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="642ae-108">Přijímá velikost objektu BLOB hodnoty v bajtech.</span><span class="sxs-lookup"><span data-stu-id="642ae-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="642ae-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="642ae-109">Return Value</span></span>  
 <span data-ttu-id="642ae-110">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="642ae-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="642ae-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="642ae-111">Requirements</span></span>  
 <span data-ttu-id="642ae-112">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="642ae-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="642ae-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="642ae-113">See also</span></span>

- [<span data-ttu-id="642ae-114">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="642ae-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="642ae-115">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="642ae-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="642ae-116">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="642ae-116">ALink API</span></span>](index.md)
