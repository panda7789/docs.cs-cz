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
ms.openlocfilehash: 14a8acc2e3babd376cb9754d35ce8fc5eaa1fd7c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492319"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="2103f-102">ISymUnmanagedWriter3::OpenMethod2 – metoda</span><span class="sxs-lookup"><span data-stu-id="2103f-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="2103f-103">Otevře metodu a poskytuje skutečné části posun v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="2103f-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2103f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2103f-104">Syntax</span></span>  
  
```  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2103f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2103f-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="2103f-106">[in] Token metadat pro metodu otevřít.</span><span class="sxs-lookup"><span data-stu-id="2103f-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="2103f-107">[in] Posun části v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="2103f-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="2103f-108">[in] Posun v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="2103f-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2103f-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2103f-109">Return Value</span></span>  
 <span data-ttu-id="2103f-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="2103f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2103f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2103f-111">Requirements</span></span>  
 <span data-ttu-id="2103f-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2103f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2103f-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2103f-113">See also</span></span>
- [<span data-ttu-id="2103f-114">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2103f-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="2103f-115">OpenMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="2103f-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
