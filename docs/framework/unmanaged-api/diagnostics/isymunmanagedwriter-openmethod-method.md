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
ms.openlocfilehash: 25178b5ea27aac7229ab51a167283d955b89addc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777260"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="1f9a1-102">ISymUnmanagedWriter::OpenMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="1f9a1-102">ISymUnmanagedWriter::OpenMethod Method</span></span>
<span data-ttu-id="1f9a1-103">Otevře se metoda, do které symbol je vygenerován informace.</span><span class="sxs-lookup"><span data-stu-id="1f9a1-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="1f9a1-104">Dané metody se změní aktuální metoda pro volání zadat body sekvence, parametry a lexikální obory.</span><span class="sxs-lookup"><span data-stu-id="1f9a1-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="1f9a1-105">Existuje implicitní lexikální prostor kolem celou metodu.</span><span class="sxs-lookup"><span data-stu-id="1f9a1-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="1f9a1-106">Znovu metodu, která dříve byla uzavřena vymaže všechny dříve definované symboly pro danou metodu.</span><span class="sxs-lookup"><span data-stu-id="1f9a1-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="1f9a1-107">Najednou lze otevřít pouze jednu metodu.</span><span class="sxs-lookup"><span data-stu-id="1f9a1-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f9a1-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f9a1-108">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f9a1-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f9a1-109">Parameters</span></span>  
 `method`  
 <span data-ttu-id="1f9a1-110">[in] Token metadat pro metodu otevřít.</span><span class="sxs-lookup"><span data-stu-id="1f9a1-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f9a1-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1f9a1-111">Return Value</span></span>  
 <span data-ttu-id="1f9a1-112">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="1f9a1-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f9a1-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1f9a1-113">Requirements</span></span>  
 <span data-ttu-id="1f9a1-114">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1f9a1-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f9a1-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f9a1-115">See also</span></span>

- [<span data-ttu-id="1f9a1-116">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1f9a1-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="1f9a1-117">CloseMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="1f9a1-117">CloseMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)
- [<span data-ttu-id="1f9a1-118">OpenMethod2 – metoda</span><span class="sxs-lookup"><span data-stu-id="1f9a1-118">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
