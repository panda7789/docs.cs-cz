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
ms.openlocfilehash: 59ec4d9f39362f563312a9ed75bb1ab5cede799d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484027"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="eefd1-102">ISymUnmanagedDocumentWriter::SetCheckSum – metoda</span><span class="sxs-lookup"><span data-stu-id="eefd1-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="eefd1-103">Nastaví údaj o kontrolním součtu.</span><span class="sxs-lookup"><span data-stu-id="eefd1-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eefd1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eefd1-104">Syntax</span></span>  
  
```  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eefd1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eefd1-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="eefd1-106">[in] Identifikátor GUID, který zastupuje identifikátor algoritmu.</span><span class="sxs-lookup"><span data-stu-id="eefd1-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="eefd1-107">[in] A `ULONG32` určující velikost v bajtech, nástroje `checkSum` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="eefd1-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="eefd1-108">[in] Vyrovnávací paměť, která ukládá informace kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="eefd1-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eefd1-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="eefd1-109">Return Value</span></span>  
 <span data-ttu-id="eefd1-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="eefd1-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eefd1-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eefd1-111">Requirements</span></span>  
 <span data-ttu-id="eefd1-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="eefd1-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eefd1-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eefd1-113">See also</span></span>
- [<span data-ttu-id="eefd1-114">ISymUnmanagedDocumentWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eefd1-114">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
