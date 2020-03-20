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
ms.openlocfilehash: 5a8442b1f0869e1592a05dfeeb0f5e6d583f3ea8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179386"
---
# <a name="setpekind-method"></a><span data-ttu-id="4e373-102">SetPEKind – metoda</span><span class="sxs-lookup"><span data-stu-id="4e373-102">SetPEKind Method</span></span>
<span data-ttu-id="4e373-103">Určuje přenosný spustitelný typ, buď specifický pro počítač nebo nezávislá na počítači.</span><span class="sxs-lookup"><span data-stu-id="4e373-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e373-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e373-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="4e373-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e373-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="4e373-106">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="4e373-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="4e373-107">Token souboru, pro který má být nastaven typ PE.</span><span class="sxs-lookup"><span data-stu-id="4e373-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="4e373-108">Může být `AssemblyID` NULL, pokud neoznačuje nevázaný netmodule.</span><span class="sxs-lookup"><span data-stu-id="4e373-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="4e373-109">Typ PE, jak je uvedeno ve [výčtu CorPEKind](../metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="4e373-109">The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="4e373-110">Architektura cílového počítače, jak je uvedeno v záhlaví NT.</span><span class="sxs-lookup"><span data-stu-id="4e373-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e373-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4e373-111">Return Value</span></span>  
 <span data-ttu-id="4e373-112">Vrátí S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="4e373-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e373-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4e373-113">Requirements</span></span>  
 <span data-ttu-id="4e373-114">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="4e373-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e373-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e373-115">See also</span></span>

- [<span data-ttu-id="4e373-116">GetPEKind – metoda</span><span class="sxs-lookup"><span data-stu-id="4e373-116">GetPEKind Method</span></span>](../metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="4e373-117">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e373-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="4e373-118">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e373-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="4e373-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="4e373-119">ALink API</span></span>](index.md)
