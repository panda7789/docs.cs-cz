---
title: SetAssemblyProps – metoda
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyProps
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 589bd7b2132693c89dc10ae1a5c8d0bf52ed481e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218989"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="66f65-102">SetAssemblyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="66f65-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="66f65-103">Přiřadí vlastností na úrovni sestavení.</span><span class="sxs-lookup"><span data-stu-id="66f65-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66f65-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66f65-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="66f65-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66f65-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="66f65-106">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="66f65-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="66f65-107">Soubor, který definuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="66f65-107">File that defines the property.</span></span> <span data-ttu-id="66f65-108">Může mít hodnotu NULL, pokud `AssemblyID` neznamená odvázat netmodule.</span><span class="sxs-lookup"><span data-stu-id="66f65-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="66f65-109">Určuje možnost upravit.</span><span class="sxs-lookup"><span data-stu-id="66f65-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="66f65-110">Nová hodnota možnosti.</span><span class="sxs-lookup"><span data-stu-id="66f65-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66f65-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="66f65-111">Return Value</span></span>  
 <span data-ttu-id="66f65-112">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="66f65-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66f65-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66f65-113">Requirements</span></span>  
 <span data-ttu-id="66f65-114">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="66f65-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66f65-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66f65-115">See also</span></span>

- [<span data-ttu-id="66f65-116">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66f65-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="66f65-117">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66f65-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="66f65-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="66f65-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
