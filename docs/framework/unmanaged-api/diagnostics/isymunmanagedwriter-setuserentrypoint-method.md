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
ms.openlocfilehash: 11dc050e2fe16a64db4ac95bb1386e2d90535e81
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895022"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="df892-102">ISymUnmanagedWriter::SetUserEntryPoint – metoda</span><span class="sxs-lookup"><span data-stu-id="df892-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="df892-103">Určuje uživatelsky definovanou metodu, která je vstupním bodem pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="df892-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="df892-104">Tento vstupní bod může být například hlavní metodou uživatele namísto zástupných procedur generovaných kompilátorem před Main.</span><span class="sxs-lookup"><span data-stu-id="df892-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df892-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df892-105">Syntax</span></span>  
  
```cpp  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df892-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="df892-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="df892-107">pro Token metadat pro metodu, která je vstupním bodem uživatele.</span><span class="sxs-lookup"><span data-stu-id="df892-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df892-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="df892-108">Return Value</span></span>  
 <span data-ttu-id="df892-109">S_OK, pokud je metoda úspěšná; jinak E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="df892-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df892-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="df892-110">Requirements</span></span>  
 <span data-ttu-id="df892-111">**Hlaviček** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="df892-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df892-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="df892-112">See also</span></span>

- [<span data-ttu-id="df892-113">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="df892-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
