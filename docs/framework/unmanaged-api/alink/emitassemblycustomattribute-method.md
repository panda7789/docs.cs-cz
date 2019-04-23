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
ms.openlocfilehash: 67073f04cfe981dd383369029d9a4b436929a0a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117842"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="650a0-102">EmitAssemblyCustomAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="650a0-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="650a0-103">Volání k nastavení vlastní atributy úrovně sestavení.</span><span class="sxs-lookup"><span data-stu-id="650a0-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="650a0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="650a0-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="650a0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="650a0-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="650a0-106">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="650a0-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="650a0-107">Soubor, který defiles atribut.</span><span class="sxs-lookup"><span data-stu-id="650a0-107">File that defiles the attribute.</span></span> <span data-ttu-id="650a0-108">Může mít hodnotu NULL, pokud `AssemblyID` neznamená odvázat netmodule.</span><span class="sxs-lookup"><span data-stu-id="650a0-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="650a0-109">Typ vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="650a0-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="650a0-110">Vlastní hodnota data.</span><span class="sxs-lookup"><span data-stu-id="650a0-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="650a0-111">Délka dat s vlastní hodnotou.</span><span class="sxs-lookup"><span data-stu-id="650a0-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="650a0-112">TRUE, pokud je vlastní atribut má vztah k podepsání sestavení.</span><span class="sxs-lookup"><span data-stu-id="650a0-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="650a0-113">TRUE, pokud mají být vygenerován více atributů.</span><span class="sxs-lookup"><span data-stu-id="650a0-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="650a0-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="650a0-114">Return Value</span></span>  
 <span data-ttu-id="650a0-115">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="650a0-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="650a0-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="650a0-116">Requirements</span></span>  
 <span data-ttu-id="650a0-117">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="650a0-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="650a0-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="650a0-118">See also</span></span>

- [<span data-ttu-id="650a0-119">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="650a0-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="650a0-120">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="650a0-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="650a0-121">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="650a0-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
