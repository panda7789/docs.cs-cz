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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 981048c10be27900f011afeab55d1c5eb523f734
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776677"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="22d13-102">ISymUnmanagedDocument::GetSourceRange – metoda</span><span class="sxs-lookup"><span data-stu-id="22d13-102">ISymUnmanagedDocument::GetSourceRange Method</span></span>
<span data-ttu-id="22d13-103">Vrátí zadaný rozsah vloženého zdroje do daného vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="22d13-103">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="22d13-104">Vyrovnávací paměť musí být dostatečně velký pro umístění zdroje.</span><span class="sxs-lookup"><span data-stu-id="22d13-104">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22d13-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22d13-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="22d13-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="22d13-106">Parameters</span></span>  
 `startLine`  
 <span data-ttu-id="22d13-107">[in] Počáteční řádek v aktuálním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="22d13-107">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="22d13-108">[in] Počáteční sloupec v aktuálním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="22d13-108">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="22d13-109">[in] Poslední řádek v aktuálním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="22d13-109">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="22d13-110">[in] Poslední sloupec v aktuálním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="22d13-110">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="22d13-111">[in] Velikost zdroje, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="22d13-111">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="22d13-112">[out] Ukazovat na proměnnou, která bude přijímat velikost zdroje.</span><span class="sxs-lookup"><span data-stu-id="22d13-112">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="22d13-113">[out] Velikost a délku zadaného rozsahu ve zdrojovém dokumentu, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="22d13-113">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22d13-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="22d13-114">Return Value</span></span>  
 <span data-ttu-id="22d13-115">S_OK, pokud metoda uspěje.</span><span class="sxs-lookup"><span data-stu-id="22d13-115">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22d13-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22d13-116">See also</span></span>

- [<span data-ttu-id="22d13-117">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22d13-117">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
