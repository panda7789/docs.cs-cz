---
title: "ISymUnmanagedDocument::GetCheckSum – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 19cd8881bdbd482cb420717855593d7b9583ae51
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="f17fc-102">ISymUnmanagedDocument::GetCheckSum – metoda</span><span class="sxs-lookup"><span data-stu-id="f17fc-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="f17fc-103">Získá kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="f17fc-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f17fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f17fc-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f17fc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f17fc-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="f17fc-106">[v] Délka vyrovnávací paměti poskytované `data` parametr</span><span class="sxs-lookup"><span data-stu-id="f17fc-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="f17fc-107">[out] Velikost a délka kontrolního součtu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="f17fc-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="f17fc-108">[out] Vyrovnávací paměť, která přijímá kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="f17fc-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f17fc-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f17fc-109">Return Value</span></span>  
 <span data-ttu-id="f17fc-110">S_OK, pokud metoda úspěšně. jinak kód chyby.</span><span class="sxs-lookup"><span data-stu-id="f17fc-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f17fc-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="f17fc-111">See Also</span></span>  
 [<span data-ttu-id="f17fc-112">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f17fc-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
