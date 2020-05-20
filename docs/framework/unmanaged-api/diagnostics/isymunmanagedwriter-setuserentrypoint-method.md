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
ms.openlocfilehash: 8b51a9dc3a968c6bd2f5f9b149f13f88dc6a1e05
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614744"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="fe700-102">ISymUnmanagedWriter::SetUserEntryPoint – metoda</span><span class="sxs-lookup"><span data-stu-id="fe700-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="fe700-103">Určuje uživatelsky definovanou metodu, která je vstupním bodem pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="fe700-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="fe700-104">Tento vstupní bod může být například hlavní metodou uživatele namísto zástupných procedur generovaných kompilátorem před Main.</span><span class="sxs-lookup"><span data-stu-id="fe700-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe700-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe700-105">Syntax</span></span>  
  
```cpp  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe700-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe700-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="fe700-107">pro Token metadat pro metodu, která je vstupním bodem uživatele.</span><span class="sxs-lookup"><span data-stu-id="fe700-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe700-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fe700-108">Return Value</span></span>  
 <span data-ttu-id="fe700-109">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="fe700-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe700-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe700-110">Requirements</span></span>  
 <span data-ttu-id="fe700-111">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fe700-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe700-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe700-112">See also</span></span>

- [<span data-ttu-id="fe700-113">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fe700-113">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
