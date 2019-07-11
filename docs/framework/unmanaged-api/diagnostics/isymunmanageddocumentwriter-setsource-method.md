---
title: ISymUnmanagedDocumentWriter::SetSource – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetSource
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetSource method [.NET Framework debugging]
- SetSource method [.NET Framework debugging]
ms.assetid: ea5b9d9f-ff06-4bd3-8de5-6435343aba59
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 555926e0e6a669f70bdeff484cff0eb62ae11f7b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776938"
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="97b8c-102">ISymUnmanagedDocumentWriter::SetSource – metoda</span><span class="sxs-lookup"><span data-stu-id="97b8c-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="97b8c-103">Nastaví vložený zdroj pro dokument, u kterého probíhá zápis.</span><span class="sxs-lookup"><span data-stu-id="97b8c-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97b8c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97b8c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97b8c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="97b8c-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="97b8c-106">[in] A `ULONG32` , který obsahuje velikost `source` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="97b8c-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="97b8c-107">[in] Vyrovnávací paměť, která ukládá vloženého zdroje.</span><span class="sxs-lookup"><span data-stu-id="97b8c-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97b8c-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="97b8c-108">Return Value</span></span>  
 <span data-ttu-id="97b8c-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="97b8c-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97b8c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="97b8c-110">Requirements</span></span>  
 <span data-ttu-id="97b8c-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="97b8c-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97b8c-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97b8c-112">See also</span></span>

- [<span data-ttu-id="97b8c-113">ISymUnmanagedDocumentWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="97b8c-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
