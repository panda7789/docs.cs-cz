---
title: ISymUnmanagedWriter3::OpenMethod2 – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.OpenMethod2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 643666df9f93d1aa5e09579359ae0db87908f10b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428330"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="f9e30-102">ISymUnmanagedWriter3::OpenMethod2 – metoda</span><span class="sxs-lookup"><span data-stu-id="f9e30-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="f9e30-103">Otevře metodu a poskytuje její skutečné části posun v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="f9e30-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9e30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9e30-104">Syntax</span></span>  
  
```  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9e30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9e30-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="f9e30-106">[v] Token metadata pro metodu chcete otevřít.</span><span class="sxs-lookup"><span data-stu-id="f9e30-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="f9e30-107">[v] Část posun v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="f9e30-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="f9e30-108">[v] Posun v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="f9e30-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9e30-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f9e30-109">Return Value</span></span>  
 <span data-ttu-id="f9e30-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="f9e30-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9e30-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9e30-111">Requirements</span></span>  
 <span data-ttu-id="f9e30-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f9e30-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9e30-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9e30-113">See Also</span></span>  
 [<span data-ttu-id="f9e30-114">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9e30-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 [<span data-ttu-id="f9e30-115">OpenMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="f9e30-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
