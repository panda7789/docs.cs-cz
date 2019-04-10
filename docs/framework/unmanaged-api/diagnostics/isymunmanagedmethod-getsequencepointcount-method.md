---
title: ISymUnmanagedMethod::GetSequencePointCount – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePointCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePointCount
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePointCount method [.NET Framework debugging]
- GetSequencePointCount method [.NET Framework debugging]
ms.assetid: 836133e8-6108-4b9b-b0a9-bce4e08dccda
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9eac17ec9599caba88ddaa73d28abcae538a4d19
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215063"
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a><span data-ttu-id="2da68-102">ISymUnmanagedMethod::GetSequencePointCount – metoda</span><span class="sxs-lookup"><span data-stu-id="2da68-102">ISymUnmanagedMethod::GetSequencePointCount Method</span></span>
<span data-ttu-id="2da68-103">Získá počet body sekvence v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="2da68-103">Gets the count of sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2da68-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2da68-104">Syntax</span></span>  
  
```  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2da68-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2da68-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="2da68-106">[out] Ukazatel `ULONG32` , která obdrží velikost vyrovnávací paměti musí obsahovat body sekvence.</span><span class="sxs-lookup"><span data-stu-id="2da68-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the sequence points.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2da68-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2da68-107">Return Value</span></span>  
 <span data-ttu-id="2da68-108">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="2da68-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2da68-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2da68-109">Requirements</span></span>  
 <span data-ttu-id="2da68-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2da68-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2da68-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2da68-111">See also</span></span>

- [<span data-ttu-id="2da68-112">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2da68-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
