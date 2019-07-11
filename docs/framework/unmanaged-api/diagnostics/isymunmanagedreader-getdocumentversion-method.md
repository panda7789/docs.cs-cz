---
title: ISymUnmanagedReader::GetDocumentVersion – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: efe4d28d207625f00634087b862d76c001518c8d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777034"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a><span data-ttu-id="27609-102">ISymUnmanagedReader::GetDocumentVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="27609-102">ISymUnmanagedReader::GetDocumentVersion Method</span></span>
<span data-ttu-id="27609-103">Načte zadanou verzi zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="27609-103">Gets the specified version of the specified document.</span></span> <span data-ttu-id="27609-104">Verze dokumentu začíná 1 a se zvýší pokaždé, když je dokument aktualizovat pomocí [updatesymbolstore –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="27609-104">The document version starts at 1 and is incremented each time the document is updated using the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method.</span></span> <span data-ttu-id="27609-105">Pokud `pbCurrent` parametr `true`, toto je nejnovější verze dokumentu.</span><span class="sxs-lookup"><span data-stu-id="27609-105">If the `pbCurrent` parameter is `true`, this is the latest version of the document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27609-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27609-106">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27609-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="27609-107">Parameters</span></span>  
 `pDoc`  
 <span data-ttu-id="27609-108">[in] Zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="27609-108">[in] The specified document.</span></span>  
  
 `version`  
 <span data-ttu-id="27609-109">[out] Ukazovat na proměnnou, která přijímá verzi zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="27609-109">[out] A pointer to a variable that receives the version of the specified document.</span></span>  
  
 `pbCurrent`  
 <span data-ttu-id="27609-110">[out] Ukazatel na proměnnou, která přijímá `true` Pokud je to nejnovější verzi dokumentu, nebo `false` Pokud ještě není na nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="27609-110">[out] A pointer to a variable that receives `true` if this is the latest version of the document, or `false` if it isn't the latest version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27609-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="27609-111">Return Value</span></span>  
 <span data-ttu-id="27609-112">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="27609-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27609-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="27609-113">Requirements</span></span>  
 <span data-ttu-id="27609-114">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="27609-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27609-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27609-115">See also</span></span>

- [<span data-ttu-id="27609-116">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="27609-116">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
