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
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="1561b-102">ISymUnmanagedMethod::GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="1561b-102">ISymUnmanagedMethod::GetToken Method</span></span>
<span data-ttu-id="1561b-103">Vrátí token metadat pro tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="1561b-103">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1561b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1561b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1561b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1561b-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="1561b-106">mimo Ukazatel na `mdMethodDef`, který obdrží velikost vyrovnávací paměti, která je nutná k uložení metadat.</span><span class="sxs-lookup"><span data-stu-id="1561b-106">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1561b-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1561b-107">Return Value</span></span>  
 <span data-ttu-id="1561b-108">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="1561b-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1561b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1561b-109">Requirements</span></span>  
 <span data-ttu-id="1561b-110">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1561b-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1561b-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1561b-111">See also</span></span>

- [<span data-ttu-id="1561b-112">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1561b-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
