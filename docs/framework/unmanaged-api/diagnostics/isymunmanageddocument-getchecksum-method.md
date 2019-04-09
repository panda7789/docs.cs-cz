---
title: ISymUnmanagedDocument::GetCheckSum – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a60bf279c143559e7410d8dfd8213d3da1d05a6d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127554"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="ae264-102">ISymUnmanagedDocument::GetCheckSum – metoda</span><span class="sxs-lookup"><span data-stu-id="ae264-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="ae264-103">Získá kontrolní součet.</span><span class="sxs-lookup"><span data-stu-id="ae264-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae264-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae264-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae264-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae264-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="ae264-106">[in] Délka vyrovnávací paměti poskytované `data` parametr</span><span class="sxs-lookup"><span data-stu-id="ae264-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="ae264-107">[out] Velikost a délce kontrolní součet v bajtech.</span><span class="sxs-lookup"><span data-stu-id="ae264-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="ae264-108">[out] Vyrovnávací paměť, která přijímá kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="ae264-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae264-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ae264-109">Return Value</span></span>  
 <span data-ttu-id="ae264-110">Pokud metoda uspěje; S_OK v opačném případě chybový kód.</span><span class="sxs-lookup"><span data-stu-id="ae264-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae264-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae264-111">See also</span></span>

- [<span data-ttu-id="ae264-112">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ae264-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
