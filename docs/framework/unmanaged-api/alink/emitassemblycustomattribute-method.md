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
ms.openlocfilehash: bb21ee1396a9dd0426b9b91711c2345ef66c09f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="b5df7-102">EmitAssemblyCustomAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="b5df7-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="b5df7-103">Volání nastavení úrovně sestavení vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="b5df7-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5df7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5df7-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="b5df7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5df7-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b5df7-106">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="b5df7-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="b5df7-107">Soubor, který defiles atribut.</span><span class="sxs-lookup"><span data-stu-id="b5df7-107">File that defiles the attribute.</span></span> <span data-ttu-id="b5df7-108">Může mít hodnotu NULL, pokud `AssemblyID` neindikuje nevázaný netmodule.</span><span class="sxs-lookup"><span data-stu-id="b5df7-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="b5df7-109">Typ vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="b5df7-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="b5df7-110">Vlastní hodnota data.</span><span class="sxs-lookup"><span data-stu-id="b5df7-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="b5df7-111">Délka dat vlastní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b5df7-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="b5df7-112">Hodnota TRUE, pokud vlastní atribut má vztah k podepsání sestavení.</span><span class="sxs-lookup"><span data-stu-id="b5df7-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="b5df7-113">Hodnota TRUE, pokud mají být vygenerované více atributů.</span><span class="sxs-lookup"><span data-stu-id="b5df7-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5df7-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b5df7-114">Return Value</span></span>  
 <span data-ttu-id="b5df7-115">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="b5df7-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5df7-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b5df7-116">Requirements</span></span>  
 <span data-ttu-id="b5df7-117">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="b5df7-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5df7-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5df7-118">See Also</span></span>  
 [<span data-ttu-id="b5df7-119">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b5df7-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="b5df7-120">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b5df7-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="b5df7-121">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="b5df7-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
