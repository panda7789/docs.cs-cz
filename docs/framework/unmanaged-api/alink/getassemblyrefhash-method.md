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
ms.openlocfilehash: c68f43ce2f79ee6e4ec44ce4b2f0dbfb1c1185fa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433870"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="a2f05-102">GetAssemblyRefHash – metoda</span><span class="sxs-lookup"><span data-stu-id="a2f05-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="a2f05-103">Načte objekt BLOB algoritmu hash pro dané sestavení.</span><span class="sxs-lookup"><span data-stu-id="a2f05-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2f05-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2f05-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2f05-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2f05-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="a2f05-106">ID sestavení, na které bude odkazovat hodnota hash</span><span class="sxs-lookup"><span data-stu-id="a2f05-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="a2f05-107">Přijímá výsledný objekt BLOB algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="a2f05-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="a2f05-108">Přijímá velikost objektu BLOB hodnoty v bajtech.</span><span class="sxs-lookup"><span data-stu-id="a2f05-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2f05-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a2f05-109">Return Value</span></span>  
 <span data-ttu-id="a2f05-110">Vrátí S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="a2f05-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2f05-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a2f05-111">Requirements</span></span>  
 <span data-ttu-id="a2f05-112">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="a2f05-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2f05-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a2f05-113">See also</span></span>

- [<span data-ttu-id="a2f05-114">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a2f05-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="a2f05-115">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a2f05-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="a2f05-116">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="a2f05-116">ALink API</span></span>](index.md)
