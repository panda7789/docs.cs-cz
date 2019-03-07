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
ms.openlocfilehash: e568050a5cc94da865d656adc8a775024dab836c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500041"
---
# <a name="setpekind-method"></a><span data-ttu-id="057b8-102">SetPEKind – metoda</span><span class="sxs-lookup"><span data-stu-id="057b8-102">SetPEKind Method</span></span>
<span data-ttu-id="057b8-103">Určuje specifické pro počítač nebo počítač bez ohledu na typ přenosný spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="057b8-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="057b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="057b8-104">Syntax</span></span>  
  
```  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="057b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="057b8-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="057b8-106">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="057b8-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="057b8-107">Token souboru, pro který má být nastavena typu PE.</span><span class="sxs-lookup"><span data-stu-id="057b8-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="057b8-108">Může mít hodnotu NULL, pokud `AssemblyID` neznamená odvázat netmodule.</span><span class="sxs-lookup"><span data-stu-id="057b8-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="057b8-109">Typ systému PE, je určeno [corpekind – výčet](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="057b8-109">The type of PE, as indicated by the [CorPEKind Enumeration](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="057b8-110">Architektury cílového počítače, jak je uvedeno v hlavičce NT.</span><span class="sxs-lookup"><span data-stu-id="057b8-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="057b8-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="057b8-111">Return Value</span></span>  
 <span data-ttu-id="057b8-112">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="057b8-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="057b8-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="057b8-113">Requirements</span></span>  
 <span data-ttu-id="057b8-114">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="057b8-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="057b8-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="057b8-115">See also</span></span>
- [<span data-ttu-id="057b8-116">GetPEKind – metoda</span><span class="sxs-lookup"><span data-stu-id="057b8-116">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="057b8-117">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="057b8-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="057b8-118">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="057b8-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="057b8-119">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="057b8-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
