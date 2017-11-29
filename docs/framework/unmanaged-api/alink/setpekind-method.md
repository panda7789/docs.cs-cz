---
title: "SetPEKind – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.SetPEKind
api_location: alink.dll
api_type: COM
f1_keywords: SetPEKind
helpviewer_keywords: SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d511bcda2ab4e879c123d866b3f6c887173c1d2f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="setpekind-method"></a><span data-ttu-id="3c5f5-102">SetPEKind – metoda</span><span class="sxs-lookup"><span data-stu-id="3c5f5-102">SetPEKind Method</span></span>
<span data-ttu-id="3c5f5-103">Určuje konkrétní počítač nebo počítače bez ohledu na typ přenosné spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="3c5f5-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c5f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c5f5-104">Syntax</span></span>  
  
```  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c5f5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c5f5-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="3c5f5-106">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="3c5f5-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="3c5f5-107">Token souboru, pro kterou má být nastavena typ PE.</span><span class="sxs-lookup"><span data-stu-id="3c5f5-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="3c5f5-108">Může mít hodnotu NULL, pokud `AssemblyID` neindikuje nevázaný netmodule.</span><span class="sxs-lookup"><span data-stu-id="3c5f5-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="3c5f5-109">Typ PE, jak [CorPEKind – výčet](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="3c5f5-109">The type of PE, as indicated by the [CorPEKind Enumeration](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="3c5f5-110">Architektury cílového počítače, jak je uvedeno v hlavičce NT.</span><span class="sxs-lookup"><span data-stu-id="3c5f5-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c5f5-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3c5f5-111">Return Value</span></span>  
 <span data-ttu-id="3c5f5-112">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="3c5f5-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c5f5-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3c5f5-113">Requirements</span></span>  
 <span data-ttu-id="3c5f5-114">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="3c5f5-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c5f5-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c5f5-115">See Also</span></span>  
 [<span data-ttu-id="3c5f5-116">GetPEKind – metoda</span><span class="sxs-lookup"><span data-stu-id="3c5f5-116">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)  
 [<span data-ttu-id="3c5f5-117">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c5f5-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="3c5f5-118">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c5f5-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="3c5f5-119">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="3c5f5-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
