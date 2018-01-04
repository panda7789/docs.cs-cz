---
title: "ISymUnmanagedWriter::OpenNamespace – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.OpenNamespace
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::OpenNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::OpenNamespace method [.NET Framework debugging]
- OpenNamespace method [.NET Framework debugging]
ms.assetid: 426f4e4f-e60d-4ad1-b546-a10e3c55c283
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 77d50f6bac87d5a110b53a69044f96f547c51904
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="a7a8b-102">ISymUnmanagedWriter::OpenNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="a7a8b-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="a7a8b-103">Otevře se nový obor názvů.</span><span class="sxs-lookup"><span data-stu-id="a7a8b-103">Opens a new namespace.</span></span> <span data-ttu-id="a7a8b-104">Tuto metodu volejte před definováním metody nebo proměnné, které zabírají obor názvů.</span><span class="sxs-lookup"><span data-stu-id="a7a8b-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="a7a8b-105">Mohou být vnořené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="a7a8b-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7a8b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7a8b-106">Syntax</span></span>  
  
```  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7a8b-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7a8b-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="a7a8b-108">[v] Ukazatel na název nového oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a7a8b-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7a8b-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a7a8b-109">Return Value</span></span>  
 <span data-ttu-id="a7a8b-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="a7a8b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7a8b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a7a8b-111">Requirements</span></span>  
 <span data-ttu-id="a7a8b-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a7a8b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a8b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7a8b-113">See Also</span></span>  
 [<span data-ttu-id="a7a8b-114">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a7a8b-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="a7a8b-115">CloseNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="a7a8b-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)
