---
title: ISymENCUnmanagedMethod::GetDocumentsForMethod – metoda
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethod
helpviewer_keywords:
- GetDocumentsForMethod method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethod method [.NET Framework debugging]
ms.assetid: bd6ccde5-d578-48d8-abed-b474fbd48d13
topic_type:
- apiref
ms.openlocfilehash: 89be772ee3d8a6fc5acb74d5ebe6d3c691764f89
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441952"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="d0d28-102">ISymENCUnmanagedMethod::GetDocumentsForMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="d0d28-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="d0d28-103">Načte dokumenty, ve kterých tato metoda obsahuje řádky.</span><span class="sxs-lookup"><span data-stu-id="d0d28-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0d28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0d28-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0d28-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0d28-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="d0d28-106">pro Délka vyrovnávací paměti, na kterou ukazuje `pcDocs` .</span><span class="sxs-lookup"><span data-stu-id="d0d28-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="d0d28-107">mimo Ukazatel na `ULONG32` , který přijímá velikost vyrovnávací paměti, která je nutná k uložení dokumentů v počtu znaků.</span><span class="sxs-lookup"><span data-stu-id="d0d28-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="d0d28-108">pro Vyrovnávací paměť, která obsahuje dokumenty.</span><span class="sxs-lookup"><span data-stu-id="d0d28-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0d28-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d0d28-109">Return Value</span></span>  
 <span data-ttu-id="d0d28-110">S_OK, pokud je metoda úspěšná; v opačném případě kód chyby.</span><span class="sxs-lookup"><span data-stu-id="d0d28-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0d28-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d0d28-111">Requirements</span></span>  
 <span data-ttu-id="d0d28-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d0d28-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0d28-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0d28-113">See also</span></span>

- [<span data-ttu-id="d0d28-114">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0d28-114">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
