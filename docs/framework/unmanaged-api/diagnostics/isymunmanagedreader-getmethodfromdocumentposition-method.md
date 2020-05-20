---
title: ISymUnmanagedReader::GetMethodFromDocumentPosition – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodFromDocumentPosition
helpviewer_keywords:
- GetMethodFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 55773dbc-9053-46e3-8a3c-86caa9d91fb4
topic_type:
- apiref
ms.openlocfilehash: 8015056b110fe8a5b5122b1bc81143980b780047
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614978"
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="c7059-102">ISymUnmanagedReader::GetMethodFromDocumentPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="c7059-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="c7059-103">Vrátí metodu, která obsahuje zarážku na dané pozici v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c7059-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7059-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7059-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7059-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7059-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="c7059-106">pro Zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="c7059-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="c7059-107">pro Řádek zadaného dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c7059-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="c7059-108">pro Sloupec zadaného dokumentu</span><span class="sxs-lookup"><span data-stu-id="c7059-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="c7059-109">mimo Ukazatel na adresu objektu [rozhraní ISymUnmanagedMethod](isymunmanagedmethod-interface.md) , který představuje metodu obsahující zarážku.</span><span class="sxs-lookup"><span data-stu-id="c7059-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7059-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c7059-110">Return Value</span></span>  
 <span data-ttu-id="c7059-111">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="c7059-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7059-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7059-112">Requirements</span></span>  
 <span data-ttu-id="c7059-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c7059-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7059-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7059-114">See also</span></span>

- [<span data-ttu-id="c7059-115">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c7059-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
