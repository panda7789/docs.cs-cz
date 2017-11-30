---
title: "ISymUnmanagedDocumentWriter::SetSource – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocumentWriter.SetSource
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocumentWriter::SetSource
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetSource method [.NET Framework debugging]
- SetSource method [.NET Framework debugging]
ms.assetid: ea5b9d9f-ff06-4bd3-8de5-6435343aba59
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 74b917ff4c2853eb31625af2ab1d2c64ced613e0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="a63da-102">ISymUnmanagedDocumentWriter::SetSource – metoda</span><span class="sxs-lookup"><span data-stu-id="a63da-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="a63da-103">Nastaví vložený zdroj pro dokument, který se připravuje.</span><span class="sxs-lookup"><span data-stu-id="a63da-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a63da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a63da-104">Syntax</span></span>  
  
```  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a63da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a63da-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="a63da-106">[v] A `ULONG32` obsahující velikost `source` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a63da-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="a63da-107">[v] Vyrovnávací paměť, která ukládá vložený zdroj.</span><span class="sxs-lookup"><span data-stu-id="a63da-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a63da-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a63da-108">Return Value</span></span>  
 <span data-ttu-id="a63da-109">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="a63da-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a63da-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a63da-110">Requirements</span></span>  
 <span data-ttu-id="a63da-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a63da-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a63da-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="a63da-112">See Also</span></span>  
 [<span data-ttu-id="a63da-113">Isymunmanageddocumentwriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a63da-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
