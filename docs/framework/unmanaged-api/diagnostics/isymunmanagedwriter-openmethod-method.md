---
title: ISymUnmanagedWriter::OpenMethod – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3e6ee68fe3ffed0ae19c2f528a49a863b99fa7f7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499547"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="fda35-102">ISymUnmanagedWriter::OpenMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="fda35-102">ISymUnmanagedWriter::OpenMethod Method</span></span>
<span data-ttu-id="fda35-103">Otevře se metoda, do které symbol je vygenerován informace.</span><span class="sxs-lookup"><span data-stu-id="fda35-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="fda35-104">Dané metody se změní aktuální metoda pro volání zadat body sekvence, parametry a lexikální obory.</span><span class="sxs-lookup"><span data-stu-id="fda35-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="fda35-105">Existuje implicitní lexikální prostor kolem celou metodu.</span><span class="sxs-lookup"><span data-stu-id="fda35-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="fda35-106">Znovu metodu, která dříve byla uzavřena vymaže všechny dříve definované symboly pro danou metodu.</span><span class="sxs-lookup"><span data-stu-id="fda35-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="fda35-107">Najednou lze otevřít pouze jednu metodu.</span><span class="sxs-lookup"><span data-stu-id="fda35-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fda35-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fda35-108">Syntax</span></span>  
  
```  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fda35-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="fda35-109">Parameters</span></span>  
 `method`  
 <span data-ttu-id="fda35-110">[in] Token metadat pro metodu otevřít.</span><span class="sxs-lookup"><span data-stu-id="fda35-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fda35-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fda35-111">Return Value</span></span>  
 <span data-ttu-id="fda35-112">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="fda35-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fda35-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fda35-113">Requirements</span></span>  
 <span data-ttu-id="fda35-114">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fda35-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fda35-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fda35-115">See also</span></span>
- [<span data-ttu-id="fda35-116">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fda35-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="fda35-117">CloseMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="fda35-117">CloseMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)
- [<span data-ttu-id="fda35-118">OpenMethod2 – metoda</span><span class="sxs-lookup"><span data-stu-id="fda35-118">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
