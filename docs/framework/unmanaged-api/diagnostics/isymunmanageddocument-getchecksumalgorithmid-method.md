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
ms.openlocfilehash: a76435be591d9f73d5975c5315f6e744f8972fc7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614614"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a><span data-ttu-id="afba9-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId – metoda</span><span class="sxs-lookup"><span data-stu-id="afba9-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Method</span></span>
<span data-ttu-id="afba9-103">Získá identifikátor algoritmu kontrolního součtu nebo vrátí identifikátor GUID všech nul, pokud neexistuje kontrolní součet.</span><span class="sxs-lookup"><span data-stu-id="afba9-103">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afba9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afba9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afba9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="afba9-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="afba9-106">mimo Ukazatel na proměnnou, která přijímá identifikátor algoritmu kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="afba9-106">[out] A pointer to a variable that receives the checksum algorithm identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="afba9-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="afba9-107">Return Value</span></span>  
 <span data-ttu-id="afba9-108">S_OK, zda je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="afba9-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afba9-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="afba9-109">See also</span></span>

- [<span data-ttu-id="afba9-110">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="afba9-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
