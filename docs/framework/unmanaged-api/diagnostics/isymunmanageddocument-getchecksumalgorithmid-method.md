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
ms.openlocfilehash: 2bc673d2e331cd32d5317cb20f9418eb3a3b144a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431065"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a><span data-ttu-id="f9c08-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId – metoda</span><span class="sxs-lookup"><span data-stu-id="f9c08-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Method</span></span>
<span data-ttu-id="f9c08-103">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span><span class="sxs-lookup"><span data-stu-id="f9c08-103">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9c08-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9c08-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9c08-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9c08-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="f9c08-106">[out] A pointer to a variable that receives the checksum algorithm identifier.</span><span class="sxs-lookup"><span data-stu-id="f9c08-106">[out] A pointer to a variable that receives the checksum algorithm identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9c08-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f9c08-107">Return Value</span></span>  
 <span data-ttu-id="f9c08-108">S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="f9c08-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9c08-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9c08-109">See also</span></span>

- [<span data-ttu-id="f9c08-110">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9c08-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
