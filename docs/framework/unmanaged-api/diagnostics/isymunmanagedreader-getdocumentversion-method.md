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
ms.openlocfilehash: 92353cfc2d9ce39074bf43937b5673ff51e34822
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939422"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a><span data-ttu-id="40036-102">ISymUnmanagedReader::GetDocumentVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="40036-102">ISymUnmanagedReader::GetDocumentVersion Method</span></span>
<span data-ttu-id="40036-103">Načte zadanou verzi zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="40036-103">Gets the specified version of the specified document.</span></span> <span data-ttu-id="40036-104">Verze dokumentu začíná 1 a se zvýší pokaždé, když je dokument aktualizovat pomocí [updatesymbolstore –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="40036-104">The document version starts at 1 and is incremented each time the document is updated using the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method.</span></span> <span data-ttu-id="40036-105">Pokud `pbCurrent` parametr `true`, toto je nejnovější verze dokumentu.</span><span class="sxs-lookup"><span data-stu-id="40036-105">If the `pbCurrent` parameter is `true`, this is the latest version of the document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40036-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40036-106">Syntax</span></span>  
  
```  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40036-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="40036-107">Parameters</span></span>  
 `pDoc`  
 <span data-ttu-id="40036-108">[in] Zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="40036-108">[in] The specified document.</span></span>  
  
 `version`  
 <span data-ttu-id="40036-109">[out] Ukazovat na proměnnou, která přijímá verzi zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="40036-109">[out] A pointer to a variable that receives the version of the specified document.</span></span>  
  
 `pbCurrent`  
 <span data-ttu-id="40036-110">[out] Ukazatel na proměnnou, která přijímá `true` Pokud je to nejnovější verzi dokumentu, nebo `false` Pokud ještě není na nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="40036-110">[out] A pointer to a variable that receives `true` if this is the latest version of the document, or `false` if it isn't the latest version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40036-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="40036-111">Return Value</span></span>  
 <span data-ttu-id="40036-112">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="40036-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40036-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40036-113">Requirements</span></span>  
 <span data-ttu-id="40036-114">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="40036-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40036-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40036-115">See also</span></span>

- [<span data-ttu-id="40036-116">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40036-116">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
