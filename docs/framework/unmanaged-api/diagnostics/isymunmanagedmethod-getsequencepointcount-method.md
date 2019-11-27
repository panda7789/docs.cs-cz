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
ms.openlocfilehash: 889fd4ec3332cbe80a035e13a5145421dc0ed5a9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448891"
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a><span data-ttu-id="10955-102">ISymUnmanagedMethod::GetSequencePointCount – metoda</span><span class="sxs-lookup"><span data-stu-id="10955-102">ISymUnmanagedMethod::GetSequencePointCount Method</span></span>
<span data-ttu-id="10955-103">Získá počet bodů sekvence v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="10955-103">Gets the count of sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10955-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10955-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10955-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="10955-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="10955-106">mimo Ukazatel na `ULONG32`, který přijímá velikost vyrovnávací paměti vyžadované k umístění bodů sekvence.</span><span class="sxs-lookup"><span data-stu-id="10955-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the sequence points.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10955-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="10955-107">Return Value</span></span>  
 <span data-ttu-id="10955-108">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="10955-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10955-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="10955-109">Requirements</span></span>  
 <span data-ttu-id="10955-110">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="10955-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10955-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10955-111">See also</span></span>

- [<span data-ttu-id="10955-112">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="10955-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
