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
ms.openlocfilehash: 7595b4a69dd327e448aade1e2dcba06100e55bf4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638678"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="e6ec9-102">ISymUnmanagedWriter::SetUserEntryPoint – metoda</span><span class="sxs-lookup"><span data-stu-id="e6ec9-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="e6ec9-103">Určuje metodu definovaný uživatelem, která je vstupním bodem pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="e6ec9-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="e6ec9-104">Tento vstupní bod může být například hlavní metoda uživatele místo vygenerovaný kompilátorem zástupné procedury před hlavní.</span><span class="sxs-lookup"><span data-stu-id="e6ec9-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6ec9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6ec9-105">Syntax</span></span>  
  
```  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6ec9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e6ec9-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="e6ec9-107">[in] Bodu tokenu metadat pro metodu, která je vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="e6ec9-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6ec9-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e6ec9-108">Return Value</span></span>  
 <span data-ttu-id="e6ec9-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="e6ec9-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6ec9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e6ec9-110">Requirements</span></span>  
 <span data-ttu-id="e6ec9-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e6ec9-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6ec9-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6ec9-112">See also</span></span>
- [<span data-ttu-id="e6ec9-113">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e6ec9-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
