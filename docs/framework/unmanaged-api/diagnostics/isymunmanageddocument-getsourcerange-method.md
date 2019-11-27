---
title: ISymUnmanagedDocument::GetSourceRange – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type:
- apiref
ms.openlocfilehash: 64ecbb56ab32ac8381a4864acd5fd40741786d30
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449135"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="c3f07-102">ISymUnmanagedDocument::GetSourceRange – metoda</span><span class="sxs-lookup"><span data-stu-id="c3f07-102">ISymUnmanagedDocument::GetSourceRange Method</span></span>
<span data-ttu-id="c3f07-103">Vrátí zadaný rozsah vloženého zdroje do dané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="c3f07-103">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="c3f07-104">Vyrovnávací paměť musí být dostatečně velká pro uložení zdroje.</span><span class="sxs-lookup"><span data-stu-id="c3f07-104">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3f07-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3f07-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3f07-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3f07-106">Parameters</span></span>  
 `startLine`  
 <span data-ttu-id="c3f07-107">pro Počáteční řádek v aktuálním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c3f07-107">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="c3f07-108">pro Počáteční sloupec v aktuálním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c3f07-108">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="c3f07-109">pro Poslední řádek v aktuálním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c3f07-109">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="c3f07-110">pro Konečný sloupec v aktuálním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c3f07-110">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="c3f07-111">pro Velikost zdroje (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="c3f07-111">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="c3f07-112">mimo Ukazatel na proměnnou, která přijímá velikost zdroje.</span><span class="sxs-lookup"><span data-stu-id="c3f07-112">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="c3f07-113">mimo Velikost a délka zadaného rozsahu zdrojového dokumentu (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="c3f07-113">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3f07-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c3f07-114">Return Value</span></span>  
 <span data-ttu-id="c3f07-115">S_OK, zda je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="c3f07-115">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3f07-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3f07-116">See also</span></span>

- [<span data-ttu-id="c3f07-117">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3f07-117">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
