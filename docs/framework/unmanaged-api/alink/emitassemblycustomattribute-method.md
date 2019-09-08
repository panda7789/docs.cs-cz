---
title: EmitAssemblyCustomAttribute – metoda
ms.date: 03/30/2017
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssemblyCustomAttribute
helpviewer_keywords:
- EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 77d54f6c8f67dda5132518d1fbd579a91ce82071
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777438"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="c7156-102">EmitAssemblyCustomAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="c7156-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="c7156-103">Volání pro nastavení vlastních atributů na úrovni sestavení.</span><span class="sxs-lookup"><span data-stu-id="c7156-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7156-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7156-104">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssemblyCustomAttribute(  
    mdAssembly   AssemblyID,  
    mdToken      FileToken,  
    mdToken      tkType,  
    void const*  pCustomValue,  
    DWORD        cbCustomValue,  
    BOOL         bSecurity,  
    BOOL         bAllowMulti  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7156-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7156-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c7156-106">ID sestavení</span><span class="sxs-lookup"><span data-stu-id="c7156-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="c7156-107">Soubor, který tento atribut odfile.</span><span class="sxs-lookup"><span data-stu-id="c7156-107">File that defiles the attribute.</span></span> <span data-ttu-id="c7156-108">Může mít hodnotu null `AssemblyID` , pokud neoznačuje nevázaný netmodule.</span><span class="sxs-lookup"><span data-stu-id="c7156-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="c7156-109">Typ vlastního atributu</span><span class="sxs-lookup"><span data-stu-id="c7156-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="c7156-110">Vlastní data hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c7156-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="c7156-111">Délka dat vlastních hodnot</span><span class="sxs-lookup"><span data-stu-id="c7156-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="c7156-112">TRUE, pokud vlastní atribut souvisí s podepisováním sestavení.</span><span class="sxs-lookup"><span data-stu-id="c7156-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="c7156-113">TRUE, pokud má být vygenerováno více atributů.</span><span class="sxs-lookup"><span data-stu-id="c7156-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7156-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c7156-114">Return Value</span></span>  
 <span data-ttu-id="c7156-115">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="c7156-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7156-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7156-116">Requirements</span></span>  
 <span data-ttu-id="c7156-117">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="c7156-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7156-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7156-118">See also</span></span>

- [<span data-ttu-id="c7156-119">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c7156-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c7156-120">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c7156-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c7156-121">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="c7156-121">ALink API</span></span>](index.md)
