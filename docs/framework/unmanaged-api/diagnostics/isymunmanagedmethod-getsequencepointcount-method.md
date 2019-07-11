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
ms.openlocfilehash: 22c45ff77c030dcbe87e5aa53284b2cace9849ab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759476"
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a><span data-ttu-id="09f50-102">ISymUnmanagedMethod::GetSequencePointCount – metoda</span><span class="sxs-lookup"><span data-stu-id="09f50-102">ISymUnmanagedMethod::GetSequencePointCount Method</span></span>
<span data-ttu-id="09f50-103">Získá počet body sekvence v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="09f50-103">Gets the count of sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09f50-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09f50-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09f50-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09f50-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="09f50-106">[out] Ukazatel `ULONG32` , která obdrží velikost vyrovnávací paměti musí obsahovat body sekvence.</span><span class="sxs-lookup"><span data-stu-id="09f50-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the sequence points.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09f50-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="09f50-107">Return Value</span></span>  
 <span data-ttu-id="09f50-108">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="09f50-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09f50-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="09f50-109">Requirements</span></span>  
 <span data-ttu-id="09f50-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="09f50-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09f50-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="09f50-111">See also</span></span>

- [<span data-ttu-id="09f50-112">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="09f50-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
