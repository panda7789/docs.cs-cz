---
title: ISymUnmanagedDocumentWriter::SetCheckSum – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum method [.NET Framework debugging]
- SetCheckSum method [.NET Framework debugging]
ms.assetid: c7e99879-421f-43ce-b193-34733cf30085
topic_type:
- apiref
ms.openlocfilehash: 06a331e24622e0a155d974ca869818a6532baa1f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615537"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="b1a1d-102">ISymUnmanagedDocumentWriter::SetCheckSum – metoda</span><span class="sxs-lookup"><span data-stu-id="b1a1d-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="b1a1d-103">Nastaví informace kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="b1a1d-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1a1d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1a1d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1a1d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1a1d-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="b1a1d-106">pro Identifikátor GUID, který představuje identifikátor algoritmu.</span><span class="sxs-lookup"><span data-stu-id="b1a1d-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="b1a1d-107">pro `ULONG32`Který udává velikost vyrovnávací paměti v bajtech `checkSum` .</span><span class="sxs-lookup"><span data-stu-id="b1a1d-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="b1a1d-108">pro Vyrovnávací paměť, do které jsou uloženy informace kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="b1a1d-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1a1d-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b1a1d-109">Return Value</span></span>  
 <span data-ttu-id="b1a1d-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="b1a1d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1a1d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1a1d-111">Requirements</span></span>  
 <span data-ttu-id="b1a1d-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b1a1d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1a1d-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1a1d-113">See also</span></span>

- [<span data-ttu-id="b1a1d-114">ISymUnmanagedDocumentWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b1a1d-114">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)
