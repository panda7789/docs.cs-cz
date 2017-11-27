---
title: "ISymUnmanagedWriter::OpenNamespace – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.OpenNamespace
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::OpenNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::OpenNamespace method [.NET Framework debugging]
- OpenNamespace method [.NET Framework debugging]
ms.assetid: 426f4e4f-e60d-4ad1-b546-a10e3c55c283
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e3dffd9605bd238446156d7a32e8e668ddd80916
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="f0ee2-102">ISymUnmanagedWriter::OpenNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="f0ee2-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="f0ee2-103">Otevře se nový obor názvů.</span><span class="sxs-lookup"><span data-stu-id="f0ee2-103">Opens a new namespace.</span></span> <span data-ttu-id="f0ee2-104">Tuto metodu volejte před definováním metody nebo proměnné, které zabírají obor názvů.</span><span class="sxs-lookup"><span data-stu-id="f0ee2-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="f0ee2-105">Mohou být vnořené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="f0ee2-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0ee2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0ee2-106">Syntax</span></span>  
  
```  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0ee2-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0ee2-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="f0ee2-108">[v] Ukazatel na název nového oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f0ee2-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0ee2-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f0ee2-109">Return Value</span></span>  
 <span data-ttu-id="f0ee2-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="f0ee2-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0ee2-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f0ee2-111">Requirements</span></span>  
 <span data-ttu-id="f0ee2-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f0ee2-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0ee2-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0ee2-113">See Also</span></span>  
 [<span data-ttu-id="f0ee2-114">ISymUnmanagedWriter – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="f0ee2-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="f0ee2-115">Closenamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="f0ee2-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)
