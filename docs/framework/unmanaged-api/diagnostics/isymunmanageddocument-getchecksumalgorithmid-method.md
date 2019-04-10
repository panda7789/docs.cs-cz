---
title: ISymUnmanagedDocument::GetCheckSumAlgorithmId – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSumAlgorithmId
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId method [.NET Framework debugging]
- GetCheckSumAlgorithmId method [.NET Framework debugging]
ms.assetid: c7f941cd-e25b-4b85-b1ce-5f77c9208fa9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f2df98728eec28ffca05b2e246575fc5c882a078
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229638"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a><span data-ttu-id="a2a8f-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId – metoda</span><span class="sxs-lookup"><span data-stu-id="a2a8f-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Method</span></span>
<span data-ttu-id="a2a8f-103">Získá identifikátor algoritmu kontrolního součtu, nebo vrátí identifikátor GUID samými nulami, pokud neexistuje žádné kontrolní součet.</span><span class="sxs-lookup"><span data-stu-id="a2a8f-103">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2a8f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2a8f-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2a8f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2a8f-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a2a8f-106">[out] Ukazovat na proměnnou, která přijímá identifikátor algoritmu kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="a2a8f-106">[out] A pointer to a variable that receives the checksum algorithm identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2a8f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a2a8f-107">Return Value</span></span>  
 <span data-ttu-id="a2a8f-108">S_OK, pokud metoda uspěje.</span><span class="sxs-lookup"><span data-stu-id="a2a8f-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2a8f-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a2a8f-109">See also</span></span>

- [<span data-ttu-id="a2a8f-110">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a2a8f-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
