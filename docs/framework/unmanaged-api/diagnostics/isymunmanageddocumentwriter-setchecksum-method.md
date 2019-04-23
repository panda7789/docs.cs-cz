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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ac3daccfade4f5ae10fe2ebbf83a7a11af34b89b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196980"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="bc441-102">ISymUnmanagedDocumentWriter::SetCheckSum – metoda</span><span class="sxs-lookup"><span data-stu-id="bc441-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="bc441-103">Nastaví údaj o kontrolním součtu.</span><span class="sxs-lookup"><span data-stu-id="bc441-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc441-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc441-104">Syntax</span></span>  
  
```  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc441-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc441-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="bc441-106">[in] Identifikátor GUID, který zastupuje identifikátor algoritmu.</span><span class="sxs-lookup"><span data-stu-id="bc441-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="bc441-107">[in] A `ULONG32` určující velikost v bajtech, nástroje `checkSum` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="bc441-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="bc441-108">[in] Vyrovnávací paměť, která ukládá informace kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="bc441-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc441-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bc441-109">Return Value</span></span>  
 <span data-ttu-id="bc441-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="bc441-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc441-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bc441-111">Requirements</span></span>  
 <span data-ttu-id="bc441-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bc441-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc441-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc441-113">See also</span></span>

- [<span data-ttu-id="bc441-114">ISymUnmanagedDocumentWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bc441-114">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
