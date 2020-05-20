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
ms.openlocfilehash: ab248c6a624fbed1a6783383566be093c449ff97
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609882"
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="28bcc-102">ISymUnmanagedWriter::OpenNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="28bcc-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="28bcc-103">Otevře nový obor názvů.</span><span class="sxs-lookup"><span data-stu-id="28bcc-103">Opens a new namespace.</span></span> <span data-ttu-id="28bcc-104">Před definováním metod nebo proměnných, které zabírají obor názvů, zavolejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="28bcc-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="28bcc-105">Obory názvů můžou být vnořené.</span><span class="sxs-lookup"><span data-stu-id="28bcc-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28bcc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28bcc-106">Syntax</span></span>  
  
```cpp  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28bcc-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="28bcc-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="28bcc-108">pro Ukazatel na název nového oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="28bcc-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28bcc-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="28bcc-109">Return Value</span></span>  
 <span data-ttu-id="28bcc-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="28bcc-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28bcc-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="28bcc-111">Requirements</span></span>  
 <span data-ttu-id="28bcc-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="28bcc-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28bcc-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="28bcc-113">See also</span></span>

- [<span data-ttu-id="28bcc-114">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28bcc-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="28bcc-115">CloseNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="28bcc-115">CloseNamespace Method</span></span>](isymunmanagedwriter-closenamespace-method.md)
