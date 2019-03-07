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
ms.openlocfilehash: 5b0acee31017fd02ac3e51f9e585669b9c90ec48
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57467011"
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="67cd3-102">ISymUnmanagedMethod::GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="67cd3-102">ISymUnmanagedMethod::GetToken Method</span></span>
<span data-ttu-id="67cd3-103">Vrátí token metadat pro tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="67cd3-103">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67cd3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67cd3-104">Syntax</span></span>  
  
```  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67cd3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="67cd3-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="67cd3-106">[out] Ukazatel `mdMethodDef` , která obdrží velikost ve znacích, vyrovnávací paměti musí obsahovat metadata.</span><span class="sxs-lookup"><span data-stu-id="67cd3-106">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67cd3-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="67cd3-107">Return Value</span></span>  
 <span data-ttu-id="67cd3-108">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="67cd3-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67cd3-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="67cd3-109">Requirements</span></span>  
 <span data-ttu-id="67cd3-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="67cd3-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67cd3-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="67cd3-111">See also</span></span>
- [<span data-ttu-id="67cd3-112">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="67cd3-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
