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
ms.openlocfilehash: 7ec6e25452a40ae67570badde8a883878d103f95
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187395"
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="11a0a-102">ISymUnmanagedMethod::GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="11a0a-102">ISymUnmanagedMethod::GetToken Method</span></span>
<span data-ttu-id="11a0a-103">Vrátí token metadat pro tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="11a0a-103">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11a0a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11a0a-104">Syntax</span></span>  
  
```  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11a0a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11a0a-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="11a0a-106">[out] Ukazatel `mdMethodDef` , která obdrží velikost ve znacích, vyrovnávací paměti musí obsahovat metadata.</span><span class="sxs-lookup"><span data-stu-id="11a0a-106">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11a0a-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="11a0a-107">Return Value</span></span>  
 <span data-ttu-id="11a0a-108">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="11a0a-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11a0a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="11a0a-109">Requirements</span></span>  
 <span data-ttu-id="11a0a-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="11a0a-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11a0a-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11a0a-111">See also</span></span>

- [<span data-ttu-id="11a0a-112">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11a0a-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
