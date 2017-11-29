---
title: "ISymUnmanagedDocumentWriter::SetCheckSum – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocumentWriter.SetCheckSum
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocumentWriter::SetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum method [.NET Framework debugging]
- SetCheckSum method [.NET Framework debugging]
ms.assetid: c7e99879-421f-43ce-b193-34733cf30085
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9693b21c2b3819096ec4aeb0a275fccf76307de0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="53bcb-102">ISymUnmanagedDocumentWriter::SetCheckSum – metoda</span><span class="sxs-lookup"><span data-stu-id="53bcb-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="53bcb-103">Nastaví údaj o kontrolním součtu.</span><span class="sxs-lookup"><span data-stu-id="53bcb-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53bcb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53bcb-104">Syntax</span></span>  
  
```  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53bcb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53bcb-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="53bcb-106">[v] Identifikátor GUID, který reprezentuje identifikátor algoritmu.</span><span class="sxs-lookup"><span data-stu-id="53bcb-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="53bcb-107">[v] A `ULONG32` určující velikost v bajtech z `checkSum` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="53bcb-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="53bcb-108">[v] Vyrovnávací paměť, která ukládá informace o kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="53bcb-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53bcb-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="53bcb-109">Return Value</span></span>  
 <span data-ttu-id="53bcb-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="53bcb-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53bcb-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="53bcb-111">Requirements</span></span>  
 <span data-ttu-id="53bcb-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="53bcb-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53bcb-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="53bcb-113">See Also</span></span>  
 [<span data-ttu-id="53bcb-114">Isymunmanageddocumentwriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="53bcb-114">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
