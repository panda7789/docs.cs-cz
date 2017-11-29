---
title: "ISymUnmanagedDocument::GetLanguageVendor – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetLanguageVendor
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetLanguageVendor
helpviewer_keywords:
- GetLanguageVendor method [.NET Framework debugging]
- ISymUnmanagedDocument::GetLanguageVendor method [.NET Framework debugging]
ms.assetid: 1d4b702e-4922-441d-8b44-03804284f70b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 72fffae9995f44be9a9359c16bb876d79c9a8242
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgetlanguagevendor-method"></a><span data-ttu-id="acf41-102">ISymUnmanagedDocument::GetLanguageVendor – metoda</span><span class="sxs-lookup"><span data-stu-id="acf41-102">ISymUnmanagedDocument::GetLanguageVendor Method</span></span>
<span data-ttu-id="acf41-103">Získá jazyk dodavatele tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="acf41-103">Gets the language vendor of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acf41-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acf41-104">Syntax</span></span>  
  
```  
HRESULT GetLanguageVendor(  
    [out, retval]  GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="acf41-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="acf41-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="acf41-106">[out] Ukazatel na proměnnou, která přijímá dodavatele jazyk.</span><span class="sxs-lookup"><span data-stu-id="acf41-106">[out] A pointer to a variable that receives the language vendor.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="acf41-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="acf41-107">Return Value</span></span>  
 <span data-ttu-id="acf41-108">S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="acf41-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acf41-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="acf41-109">See Also</span></span>  
 [<span data-ttu-id="acf41-110">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="acf41-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
