---
title: ISymUnmanagedDocument::GetLanguageVendor – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguageVendor
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguageVendor
helpviewer_keywords:
- GetLanguageVendor method [.NET Framework debugging]
- ISymUnmanagedDocument::GetLanguageVendor method [.NET Framework debugging]
ms.assetid: 1d4b702e-4922-441d-8b44-03804284f70b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cd01dcbd45ecae84ccccffb510c20f580ae8c598
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939825"
---
# <a name="isymunmanageddocumentgetlanguagevendor-method"></a><span data-ttu-id="fb10b-102">ISymUnmanagedDocument::GetLanguageVendor – metoda</span><span class="sxs-lookup"><span data-stu-id="fb10b-102">ISymUnmanagedDocument::GetLanguageVendor Method</span></span>
<span data-ttu-id="fb10b-103">Získá jazyk dodavatele tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="fb10b-103">Gets the language vendor of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb10b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb10b-104">Syntax</span></span>  
  
```  
HRESULT GetLanguageVendor(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb10b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb10b-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="fb10b-106">[out] Ukazovat na proměnnou, která přijímá dodavatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="fb10b-106">[out] A pointer to a variable that receives the language vendor.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb10b-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fb10b-107">Return Value</span></span>  
 <span data-ttu-id="fb10b-108">S_OK, pokud metoda uspěje.</span><span class="sxs-lookup"><span data-stu-id="fb10b-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb10b-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb10b-109">See also</span></span>

- [<span data-ttu-id="fb10b-110">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb10b-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
