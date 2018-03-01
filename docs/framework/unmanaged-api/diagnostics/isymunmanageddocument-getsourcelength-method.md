---
title: "ISymUnmanagedDocument::GetSourceLength – metoda"
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
- ISymUnmanagedDocument.GetSourceLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceLength
helpviewer_keywords:
- GetSourceLength method [.NET Framework debugging]
- ISymUnmanagedDocument::GetSourceLength method [.NET Framework debugging]
ms.assetid: e087dbbb-f4fb-4fbe-8292-e4f1a14d0df2
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 61d9bd99a08f428993f38fb5b6889c9659607782
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a><span data-ttu-id="270ff-102">ISymUnmanagedDocument::GetSourceLength – metoda</span><span class="sxs-lookup"><span data-stu-id="270ff-102">ISymUnmanagedDocument::GetSourceLength Method</span></span>
<span data-ttu-id="270ff-103">Získá délku, v bajtech embedded zdroje.</span><span class="sxs-lookup"><span data-stu-id="270ff-103">Gets the length, in bytes, of the embedded source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="270ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="270ff-104">Syntax</span></span>  
  
```  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="270ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="270ff-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="270ff-106">[out] Ukazatel na proměnné, která udává délku v bajtech embedded zdroje.</span><span class="sxs-lookup"><span data-stu-id="270ff-106">[out] A pointer to a variable that indicates the length, in bytes, of the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="270ff-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="270ff-107">Return Value</span></span>  
 <span data-ttu-id="270ff-108">S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="270ff-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="270ff-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="270ff-109">See Also</span></span>  
 [<span data-ttu-id="270ff-110">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="270ff-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
