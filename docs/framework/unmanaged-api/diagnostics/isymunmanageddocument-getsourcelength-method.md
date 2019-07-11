---
title: ISymUnmanagedDocument::GetSourceLength – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf79c05b3b16bb61ac59534dd83cb8eb2bb1f823
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776699"
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a><span data-ttu-id="26d42-102">ISymUnmanagedDocument::GetSourceLength – metoda</span><span class="sxs-lookup"><span data-stu-id="26d42-102">ISymUnmanagedDocument::GetSourceLength Method</span></span>
<span data-ttu-id="26d42-103">Získá délku v bajtech vloženého zdroje.</span><span class="sxs-lookup"><span data-stu-id="26d42-103">Gets the length, in bytes, of the embedded source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26d42-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26d42-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26d42-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="26d42-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="26d42-106">[out] Ukazatel na proměnnou, která označuje délku v bajtech, vloženého zdroje.</span><span class="sxs-lookup"><span data-stu-id="26d42-106">[out] A pointer to a variable that indicates the length, in bytes, of the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26d42-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="26d42-107">Return Value</span></span>  
 <span data-ttu-id="26d42-108">S_OK, pokud metoda uspěje.</span><span class="sxs-lookup"><span data-stu-id="26d42-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26d42-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26d42-109">See also</span></span>

- [<span data-ttu-id="26d42-110">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="26d42-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
