---
title: ISymUnmanagedWriter::SetUserEntryPoint – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9ec44d4c2757555c74fe7fc27c26cc5fc87c4517
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426684"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="18e87-102">ISymUnmanagedWriter::SetUserEntryPoint – metoda</span><span class="sxs-lookup"><span data-stu-id="18e87-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="18e87-103">Určuje metodu definovaný uživatelem, která je vstupní bod pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="18e87-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="18e87-104">Hlavní metody uživatele místo generované kompilátorem zástupných procedur před hlavním může být například tento vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="18e87-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18e87-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18e87-105">Syntax</span></span>  
  
```  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="18e87-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="18e87-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="18e87-107">[v] Bod token metadata pro metody, které se vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="18e87-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18e87-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="18e87-108">Return Value</span></span>  
 <span data-ttu-id="18e87-109">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="18e87-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18e87-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="18e87-110">Requirements</span></span>  
 <span data-ttu-id="18e87-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="18e87-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18e87-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="18e87-112">See Also</span></span>  
 [<span data-ttu-id="18e87-113">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18e87-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
