---
title: "ISymUnmanagedWriter::SetUserEntryPoint – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetUserEntryPoint
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5da021bce46df02789547eb7ee50133b6f4d4af6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="2b013-102">ISymUnmanagedWriter::SetUserEntryPoint – metoda</span><span class="sxs-lookup"><span data-stu-id="2b013-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="2b013-103">Určuje metodu definovaný uživatelem, která je vstupní bod pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="2b013-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="2b013-104">Hlavní metody uživatele místo generované kompilátorem zástupných procedur před hlavním může být například tento vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="2b013-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b013-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b013-105">Syntax</span></span>  
  
```  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b013-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b013-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="2b013-107">[v] Bod token metadata pro metody, které se vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="2b013-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b013-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2b013-108">Return Value</span></span>  
 <span data-ttu-id="2b013-109">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="2b013-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b013-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b013-110">Requirements</span></span>  
 <span data-ttu-id="2b013-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2b013-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b013-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="2b013-112">See Also</span></span>  
 [<span data-ttu-id="2b013-113">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b013-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
