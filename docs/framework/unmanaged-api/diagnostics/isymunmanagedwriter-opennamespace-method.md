---
title: ISymUnmanagedWriter::OpenNamespace – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::OpenNamespace method [.NET Framework debugging]
- OpenNamespace method [.NET Framework debugging]
ms.assetid: 426f4e4f-e60d-4ad1-b546-a10e3c55c283
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1585acce8bba0dff327c961f5e32ef6b46794401
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59126331"
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="0cffb-102">ISymUnmanagedWriter::OpenNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="0cffb-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="0cffb-103">Otevře se nový obor názvů.</span><span class="sxs-lookup"><span data-stu-id="0cffb-103">Opens a new namespace.</span></span> <span data-ttu-id="0cffb-104">Tuto metodu volejte před definováním metody nebo proměnné, které zabírají oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0cffb-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="0cffb-105">Mohou být vnořené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="0cffb-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cffb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0cffb-106">Syntax</span></span>  
  
```  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cffb-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="0cffb-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="0cffb-108">[in] Ukazatel na název nového oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0cffb-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0cffb-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0cffb-109">Return Value</span></span>  
 <span data-ttu-id="0cffb-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="0cffb-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cffb-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0cffb-111">Requirements</span></span>  
 <span data-ttu-id="0cffb-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0cffb-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cffb-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0cffb-113">See also</span></span>

- [<span data-ttu-id="0cffb-114">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0cffb-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="0cffb-115">CloseNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="0cffb-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)
