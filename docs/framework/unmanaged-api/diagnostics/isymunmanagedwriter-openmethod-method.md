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
ms.openlocfilehash: b05ba185a9ad4ab076d29d7d609734d41677b760
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194783"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="5d466-102">ISymUnmanagedWriter::OpenMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="5d466-102">ISymUnmanagedWriter::OpenMethod Method</span></span>
<span data-ttu-id="5d466-103">Otevře se metoda, do které symbol je vygenerován informace.</span><span class="sxs-lookup"><span data-stu-id="5d466-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="5d466-104">Dané metody se změní aktuální metoda pro volání zadat body sekvence, parametry a lexikální obory.</span><span class="sxs-lookup"><span data-stu-id="5d466-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="5d466-105">Existuje implicitní lexikální prostor kolem celou metodu.</span><span class="sxs-lookup"><span data-stu-id="5d466-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="5d466-106">Znovu metodu, která dříve byla uzavřena vymaže všechny dříve definované symboly pro danou metodu.</span><span class="sxs-lookup"><span data-stu-id="5d466-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="5d466-107">Najednou lze otevřít pouze jednu metodu.</span><span class="sxs-lookup"><span data-stu-id="5d466-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d466-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d466-108">Syntax</span></span>  
  
```  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d466-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d466-109">Parameters</span></span>  
 `method`  
 <span data-ttu-id="5d466-110">[in] Token metadat pro metodu otevřít.</span><span class="sxs-lookup"><span data-stu-id="5d466-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d466-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5d466-111">Return Value</span></span>  
 <span data-ttu-id="5d466-112">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="5d466-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d466-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5d466-113">Requirements</span></span>  
 <span data-ttu-id="5d466-114">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5d466-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d466-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d466-115">See also</span></span>

- [<span data-ttu-id="5d466-116">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d466-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="5d466-117">CloseMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="5d466-117">CloseMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)
- [<span data-ttu-id="5d466-118">OpenMethod2 – metoda</span><span class="sxs-lookup"><span data-stu-id="5d466-118">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
