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
ms.openlocfilehash: 841379702e24428a8092cfd1d2cbd3c5b4e17ba4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615602"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="fccee-102">ISymUnmanagedDocument::GetSourceRange – metoda</span><span class="sxs-lookup"><span data-stu-id="fccee-102">ISymUnmanagedDocument::GetSourceRange Method</span></span>
<span data-ttu-id="fccee-103">Vrátí zadaný rozsah vloženého zdroje do dané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="fccee-103">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="fccee-104">Vyrovnávací paměť musí být dostatečně velká pro uložení zdroje.</span><span class="sxs-lookup"><span data-stu-id="fccee-104">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fccee-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fccee-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="fccee-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fccee-106">Parameters</span></span>  
 `startLine`  
 <span data-ttu-id="fccee-107">pro Počáteční řádek v aktuálním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="fccee-107">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="fccee-108">pro Počáteční sloupec v aktuálním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="fccee-108">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="fccee-109">pro Poslední řádek v aktuálním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="fccee-109">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="fccee-110">pro Konečný sloupec v aktuálním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="fccee-110">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="fccee-111">pro Velikost zdroje (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="fccee-111">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="fccee-112">mimo Ukazatel na proměnnou, která přijímá velikost zdroje.</span><span class="sxs-lookup"><span data-stu-id="fccee-112">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="fccee-113">mimo Velikost a délka zadaného rozsahu zdrojového dokumentu (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="fccee-113">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fccee-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fccee-114">Return Value</span></span>  
 <span data-ttu-id="fccee-115">S_OK, zda je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="fccee-115">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fccee-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="fccee-116">See also</span></span>

- [<span data-ttu-id="fccee-117">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fccee-117">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
