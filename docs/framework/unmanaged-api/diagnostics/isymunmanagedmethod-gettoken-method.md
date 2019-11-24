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
ms.openlocfilehash: 048d784a55fd7c29c837a54fbd5adcdcf62a7a2c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448857"
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="bf34f-102">ISymUnmanagedMethod::GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="bf34f-102">ISymUnmanagedMethod::GetToken Method</span></span>
<span data-ttu-id="bf34f-103">Returns the metadata token for this method.</span><span class="sxs-lookup"><span data-stu-id="bf34f-103">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf34f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf34f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf34f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf34f-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="bf34f-106">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span><span class="sxs-lookup"><span data-stu-id="bf34f-106">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf34f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bf34f-107">Return Value</span></span>  
 <span data-ttu-id="bf34f-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="bf34f-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf34f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bf34f-109">Requirements</span></span>  
 <span data-ttu-id="bf34f-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bf34f-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf34f-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf34f-111">See also</span></span>

- [<span data-ttu-id="bf34f-112">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf34f-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
