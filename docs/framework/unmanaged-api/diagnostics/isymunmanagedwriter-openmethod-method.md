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
ms.openlocfilehash: bc41acd6a4f2ef2557d3b39523c5e398c887c454
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427905"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="95395-102">ISymUnmanagedWriter::OpenMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="95395-102">ISymUnmanagedWriter::OpenMethod Method</span></span>
<span data-ttu-id="95395-103">Otevře se metoda, do které symbol informace jsou vydávány.</span><span class="sxs-lookup"><span data-stu-id="95395-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="95395-104">Aktuální metoda pro volání zadat body sekvence, parametry a lexikální obory se změní na dané metody.</span><span class="sxs-lookup"><span data-stu-id="95395-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="95395-105">Existuje implicitní lexikální prostor kolem celého metoda.</span><span class="sxs-lookup"><span data-stu-id="95395-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="95395-106">Znovu metodu, která byla dříve uzavřený vymaže všechny dříve definovaném symboly pro danou metodu.</span><span class="sxs-lookup"><span data-stu-id="95395-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="95395-107">Současně lze otevřít pouze jednu metodu.</span><span class="sxs-lookup"><span data-stu-id="95395-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95395-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95395-108">Syntax</span></span>  
  
```  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="95395-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="95395-109">Parameters</span></span>  
 `method`  
 <span data-ttu-id="95395-110">[v] Token metadata pro metodu chcete otevřít.</span><span class="sxs-lookup"><span data-stu-id="95395-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95395-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="95395-111">Return Value</span></span>  
 <span data-ttu-id="95395-112">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="95395-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95395-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="95395-113">Requirements</span></span>  
 <span data-ttu-id="95395-114">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="95395-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95395-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="95395-115">See Also</span></span>  
 [<span data-ttu-id="95395-116">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95395-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="95395-117">CloseMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="95395-117">CloseMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)  
 [<span data-ttu-id="95395-118">OpenMethod2 – metoda</span><span class="sxs-lookup"><span data-stu-id="95395-118">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
