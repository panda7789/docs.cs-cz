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
ms.openlocfilehash: daf2c3dcaf16e949f8770121d8324cbfe6c7d05b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404076"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="9bbc9-102">EmitAssemblyCustomAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="9bbc9-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="9bbc9-103">Volání nastavení úrovně sestavení vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="9bbc9-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bbc9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9bbc9-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="9bbc9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9bbc9-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="9bbc9-106">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="9bbc9-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="9bbc9-107">Soubor, který defiles atribut.</span><span class="sxs-lookup"><span data-stu-id="9bbc9-107">File that defiles the attribute.</span></span> <span data-ttu-id="9bbc9-108">Může mít hodnotu NULL, pokud `AssemblyID` neindikuje nevázaný netmodule.</span><span class="sxs-lookup"><span data-stu-id="9bbc9-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="9bbc9-109">Typ vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="9bbc9-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="9bbc9-110">Vlastní hodnota data.</span><span class="sxs-lookup"><span data-stu-id="9bbc9-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="9bbc9-111">Délka dat vlastní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9bbc9-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="9bbc9-112">Hodnota TRUE, pokud vlastní atribut má vztah k podepsání sestavení.</span><span class="sxs-lookup"><span data-stu-id="9bbc9-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="9bbc9-113">Hodnota TRUE, pokud mají být vygenerované více atributů.</span><span class="sxs-lookup"><span data-stu-id="9bbc9-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9bbc9-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9bbc9-114">Return Value</span></span>  
 <span data-ttu-id="9bbc9-115">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="9bbc9-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bbc9-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9bbc9-116">Requirements</span></span>  
 <span data-ttu-id="9bbc9-117">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="9bbc9-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bbc9-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="9bbc9-118">See Also</span></span>  
 [<span data-ttu-id="9bbc9-119">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9bbc9-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="9bbc9-120">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9bbc9-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="9bbc9-121">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="9bbc9-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
