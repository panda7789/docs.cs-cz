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
ms.openlocfilehash: c2cc541b2a78f16d5ca6b19405794faa825a9d72
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615030"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a><span data-ttu-id="43b0f-102">ISymUnmanagedReader::GetDocumentVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="43b0f-102">ISymUnmanagedReader::GetDocumentVersion Method</span></span>
<span data-ttu-id="43b0f-103">Načte zadanou verzi zadaného dokumentu.</span><span class="sxs-lookup"><span data-stu-id="43b0f-103">Gets the specified version of the specified document.</span></span> <span data-ttu-id="43b0f-104">Verze dokumentu začíná 1 a při každém aktualizování dokumentu pomocí metody [UpdateSymbolStore –](isymunmanagedreader-updatesymbolstore-method.md) se zvýší.</span><span class="sxs-lookup"><span data-stu-id="43b0f-104">The document version starts at 1 and is incremented each time the document is updated using the [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) method.</span></span> <span data-ttu-id="43b0f-105">Pokud `pbCurrent` je parametr `true` , jedná se o nejnovější verzi dokumentu.</span><span class="sxs-lookup"><span data-stu-id="43b0f-105">If the `pbCurrent` parameter is `true`, this is the latest version of the document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43b0f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43b0f-106">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43b0f-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="43b0f-107">Parameters</span></span>  
 `pDoc`  
 <span data-ttu-id="43b0f-108">pro Zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="43b0f-108">[in] The specified document.</span></span>  
  
 `version`  
 <span data-ttu-id="43b0f-109">mimo Ukazatel na proměnnou, která přijímá verzi zadaného dokumentu.</span><span class="sxs-lookup"><span data-stu-id="43b0f-109">[out] A pointer to a variable that receives the version of the specified document.</span></span>  
  
 `pbCurrent`  
 <span data-ttu-id="43b0f-110">mimo Ukazatel na proměnnou, která obdrží, `true` Pokud se jedná o nejnovější verzi dokumentu, nebo pokud se `false` nejedná o nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="43b0f-110">[out] A pointer to a variable that receives `true` if this is the latest version of the document, or `false` if it isn't the latest version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43b0f-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="43b0f-111">Return Value</span></span>  
 <span data-ttu-id="43b0f-112">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="43b0f-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43b0f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="43b0f-113">Requirements</span></span>  
 <span data-ttu-id="43b0f-114">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="43b0f-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43b0f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="43b0f-115">See also</span></span>

- [<span data-ttu-id="43b0f-116">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="43b0f-116">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
