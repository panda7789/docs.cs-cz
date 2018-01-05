---
title: "EmitAssemblyCustomAttribute – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location: alink.dll
api_type: COM
f1_keywords: EmitAssemblyCustomAttribute
helpviewer_keywords: EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9cc7709ef060642f12a8bc7d048e520427a5c674
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="e58fb-102">EmitAssemblyCustomAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="e58fb-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="e58fb-103">Volání nastavení úrovně sestavení vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="e58fb-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e58fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e58fb-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="e58fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e58fb-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e58fb-106">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="e58fb-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="e58fb-107">Soubor, který defiles atribut.</span><span class="sxs-lookup"><span data-stu-id="e58fb-107">File that defiles the attribute.</span></span> <span data-ttu-id="e58fb-108">Může mít hodnotu NULL, pokud `AssemblyID` neindikuje nevázaný netmodule.</span><span class="sxs-lookup"><span data-stu-id="e58fb-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="e58fb-109">Typ vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="e58fb-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="e58fb-110">Vlastní hodnota data.</span><span class="sxs-lookup"><span data-stu-id="e58fb-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="e58fb-111">Délka dat vlastní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e58fb-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="e58fb-112">Hodnota TRUE, pokud vlastní atribut má vztah k podepsání sestavení.</span><span class="sxs-lookup"><span data-stu-id="e58fb-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="e58fb-113">Hodnota TRUE, pokud mají být vygenerované více atributů.</span><span class="sxs-lookup"><span data-stu-id="e58fb-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e58fb-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e58fb-114">Return Value</span></span>  
 <span data-ttu-id="e58fb-115">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="e58fb-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e58fb-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e58fb-116">Requirements</span></span>  
 <span data-ttu-id="e58fb-117">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="e58fb-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e58fb-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="e58fb-118">See Also</span></span>  
 [<span data-ttu-id="e58fb-119">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e58fb-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="e58fb-120">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e58fb-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="e58fb-121">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="e58fb-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
