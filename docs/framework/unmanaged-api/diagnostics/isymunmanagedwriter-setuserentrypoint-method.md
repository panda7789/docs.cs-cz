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
ms.openlocfilehash: 951fc10a4560e0b4e256312017cdcd9a389f17f5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427813"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="aad0c-102">ISymUnmanagedWriter::SetUserEntryPoint – metoda</span><span class="sxs-lookup"><span data-stu-id="aad0c-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="aad0c-103">Určuje uživatelsky definovanou metodu, která je vstupním bodem pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="aad0c-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="aad0c-104">Tento vstupní bod může být například hlavní metodou uživatele namísto zástupných procedur generovaných kompilátorem před Main.</span><span class="sxs-lookup"><span data-stu-id="aad0c-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aad0c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aad0c-105">Syntax</span></span>  
  
```cpp  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aad0c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="aad0c-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="aad0c-107">pro Token metadat pro metodu, která je vstupním bodem uživatele.</span><span class="sxs-lookup"><span data-stu-id="aad0c-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aad0c-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aad0c-108">Return Value</span></span>  
 <span data-ttu-id="aad0c-109">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="aad0c-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aad0c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aad0c-110">Requirements</span></span>  
 <span data-ttu-id="aad0c-111">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="aad0c-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aad0c-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aad0c-112">See also</span></span>

- [<span data-ttu-id="aad0c-113">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aad0c-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
