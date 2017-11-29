---
title: "ISymUnmanagedWriter3::OpenMethod2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter3.OpenMethod2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1124eac951e32dbf1cedb7926f582ec6abb99007
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="90d25-102">ISymUnmanagedWriter3::OpenMethod2 – metoda</span><span class="sxs-lookup"><span data-stu-id="90d25-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="90d25-103">Otevře metodu a poskytuje její skutečné části posun v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="90d25-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90d25-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90d25-104">Syntax</span></span>  
  
```  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90d25-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="90d25-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="90d25-106">[v] Token metadata pro metodu chcete otevřít.</span><span class="sxs-lookup"><span data-stu-id="90d25-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="90d25-107">[v] Část posun v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="90d25-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="90d25-108">[v] Posun v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="90d25-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90d25-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="90d25-109">Return Value</span></span>  
 <span data-ttu-id="90d25-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="90d25-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90d25-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90d25-111">Requirements</span></span>  
 <span data-ttu-id="90d25-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="90d25-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90d25-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="90d25-113">See Also</span></span>  
 [<span data-ttu-id="90d25-114">ISymUnmanagedWriter3 – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="90d25-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 [<span data-ttu-id="90d25-115">Openmethod – metoda</span><span class="sxs-lookup"><span data-stu-id="90d25-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
