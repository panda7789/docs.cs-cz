---
title: "ISymUnmanagedReader::GetDocumentVersion – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedReader.GetDocumentVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocumentVersion
helpviewer_keywords:
- GetDocumentVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocumentVersion method [.NET Framework debugging]
ms.assetid: a51f1f64-e084-44c5-830c-2222da5a6bbf
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f2cb0abf887abaac4d7433b52a795beca509ec61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a><span data-ttu-id="8138e-102">ISymUnmanagedReader::GetDocumentVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="8138e-102">ISymUnmanagedReader::GetDocumentVersion Method</span></span>
<span data-ttu-id="8138e-103">Získá určenou verzi zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="8138e-103">Gets the specified version of the specified document.</span></span> <span data-ttu-id="8138e-104">Verze dokumentu začíná na 1 a se zvýší pokaždé, když je dokument aktualizovat pomocí [updatesymbolstore –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="8138e-104">The document version starts at 1 and is incremented each time the document is updated using the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method.</span></span> <span data-ttu-id="8138e-105">Pokud `pbCurrent` parametr `true`, je to nejnovější verze dokumentu.</span><span class="sxs-lookup"><span data-stu-id="8138e-105">If the `pbCurrent` parameter is `true`, this is the latest version of the document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8138e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8138e-106">Syntax</span></span>  
  
```  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8138e-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="8138e-107">Parameters</span></span>  
 `pDoc`  
 <span data-ttu-id="8138e-108">[v] Zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="8138e-108">[in] The specified document.</span></span>  
  
 `version`  
 <span data-ttu-id="8138e-109">[out] Ukazatel na proměnnou, která přijímá verzi zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="8138e-109">[out] A pointer to a variable that receives the version of the specified document.</span></span>  
  
 `pbCurrent`  
 <span data-ttu-id="8138e-110">[out] Ukazatel na proměnnou, která přijímá `true` Pokud je to nejnovější verze dokumentu, nebo `false` Pokud není na nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="8138e-110">[out] A pointer to a variable that receives `true` if this is the latest version of the document, or `false` if it isn't the latest version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8138e-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8138e-111">Return Value</span></span>  
 <span data-ttu-id="8138e-112">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="8138e-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8138e-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8138e-113">Requirements</span></span>  
 <span data-ttu-id="8138e-114">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8138e-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8138e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="8138e-115">See Also</span></span>  
 [<span data-ttu-id="8138e-116">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8138e-116">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
