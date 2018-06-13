---
title: ISymUnmanagedMethod::GetToken – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetToken
helpviewer_keywords:
- ISymUnmanagedMethod::GetToken method [.NET Framework debugging]
- GetToken method, ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: 4effbe95-c36e-4a45-8b2a-ee21339415fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 89ae648e38b6349bfad0a37724a9bdc1ae05e365
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425282"
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="8d729-102">ISymUnmanagedMethod::GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="8d729-102">ISymUnmanagedMethod::GetToken Method</span></span>
<span data-ttu-id="8d729-103">Vrátí metadata token tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="8d729-103">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d729-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d729-104">Syntax</span></span>  
  
```  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d729-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d729-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="8d729-106">[out] Ukazatel na `mdMethodDef` velikostí, která přijme ve znacích vyrovnávací paměti musí obsahovat metadata.</span><span class="sxs-lookup"><span data-stu-id="8d729-106">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d729-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8d729-107">Return Value</span></span>  
 <span data-ttu-id="8d729-108">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="8d729-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d729-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d729-109">Requirements</span></span>  
 <span data-ttu-id="8d729-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8d729-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d729-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d729-111">See Also</span></span>  
 [<span data-ttu-id="8d729-112">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d729-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
