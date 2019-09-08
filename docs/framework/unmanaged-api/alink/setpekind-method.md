---
title: SetPEKind – metoda
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a48dbd38d357b668c2794ae6305ceb9cad3dcf4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787189"
---
# <a name="setpekind-method"></a><span data-ttu-id="d51de-102">SetPEKind – metoda</span><span class="sxs-lookup"><span data-stu-id="d51de-102">SetPEKind Method</span></span>
<span data-ttu-id="d51de-103">Určuje typ přenositelného spustitelného souboru, který je specifický pro konkrétní počítač nebo Machine-nezávislá.</span><span class="sxs-lookup"><span data-stu-id="d51de-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d51de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d51de-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="d51de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d51de-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d51de-106">ID sestavení</span><span class="sxs-lookup"><span data-stu-id="d51de-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="d51de-107">Token souboru, pro který má být nastaven typ PE.</span><span class="sxs-lookup"><span data-stu-id="d51de-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="d51de-108">Může mít hodnotu null `AssemblyID` , pokud neoznačuje nevázaný netmodule.</span><span class="sxs-lookup"><span data-stu-id="d51de-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="d51de-109">Typ PE, jak je uvedeno ve [výčtu CorPEKind –](../metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="d51de-109">The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="d51de-110">Architektura cílového počítače, jak je uvedeno v hlavičce NT.</span><span class="sxs-lookup"><span data-stu-id="d51de-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d51de-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d51de-111">Return Value</span></span>  
 <span data-ttu-id="d51de-112">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="d51de-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d51de-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d51de-113">Requirements</span></span>  
 <span data-ttu-id="d51de-114">Vyžaduje ALink. h.</span><span class="sxs-lookup"><span data-stu-id="d51de-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d51de-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d51de-115">See also</span></span>

- [<span data-ttu-id="d51de-116">GetPEKind – metoda</span><span class="sxs-lookup"><span data-stu-id="d51de-116">GetPEKind Method</span></span>](../metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="d51de-117">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d51de-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d51de-118">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d51de-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d51de-119">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="d51de-119">ALink API</span></span>](index.md)
