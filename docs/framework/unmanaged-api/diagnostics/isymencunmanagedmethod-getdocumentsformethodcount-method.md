---
title: ISymENCUnmanagedMethod::GetDocumentsForMethodCount – metoda
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethodCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount
helpviewer_keywords:
- GetDocumentsForMethodCount method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount method [.NET Framework debugging]
ms.assetid: cc1a823a-3ff3-4a33-b641-96edc93d2b17
topic_type:
- apiref
ms.openlocfilehash: d096101189d52401c407a4108c9c81e201d3f30d
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441939"
---
# <a name="isymencunmanagedmethodgetdocumentsformethodcount-method"></a><span data-ttu-id="40129-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount – metoda</span><span class="sxs-lookup"><span data-stu-id="40129-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Method</span></span>
<span data-ttu-id="40129-103">Získá počet dokumentů, ve kterých má tato metoda řádky.</span><span class="sxs-lookup"><span data-stu-id="40129-103">Gets the number of documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40129-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40129-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethodCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40129-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40129-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="40129-106">mimo Ukazatel na `ULONG32` , který přijímá velikost vyrovnávací paměti vyžadované k uložení dokumentů.</span><span class="sxs-lookup"><span data-stu-id="40129-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40129-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="40129-107">Return Value</span></span>  
 <span data-ttu-id="40129-108">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="40129-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40129-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40129-109">Requirements</span></span>  
 <span data-ttu-id="40129-110">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="40129-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40129-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="40129-111">See also</span></span>

- [<span data-ttu-id="40129-112">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40129-112">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
