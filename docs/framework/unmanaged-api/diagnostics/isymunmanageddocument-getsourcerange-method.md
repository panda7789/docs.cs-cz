---
title: "ISymUnmanagedDocument::GetSourceRange – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetSourceRange
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6c47f1f491b184e9abe9d56d0729100b0d9b36a7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="a5dbe-102">ISymUnmanagedDocument::GetSourceRange – metoda</span><span class="sxs-lookup"><span data-stu-id="a5dbe-102">ISymUnmanagedDocument::GetSourceRange Method</span></span>
<span data-ttu-id="a5dbe-103">Vrátí zadaný rozsah embedded zdroje do dané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-103">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="a5dbe-104">Vyrovnávací paměti musí být dostatečně velký pro uložení zdroje.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-104">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5dbe-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5dbe-105">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="a5dbe-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5dbe-106">Parameters</span></span>  
 `startLine`  
 <span data-ttu-id="a5dbe-107">[v] Počáteční řádek v aktuálním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-107">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="a5dbe-108">[v] Počáteční sloupec v aktuálním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-108">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="a5dbe-109">[v] Poslední řádek v aktuálním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-109">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="a5dbe-110">[v] Poslední sloupec v aktuálním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-110">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="a5dbe-111">[v] Velikost zdroje v bajtech.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-111">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="a5dbe-112">[out] Ukazatel na proměnnou, která přijímá velikost zdroje.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-112">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="a5dbe-113">[out] Velikost a délku zadaný rozsah zdrojový dokument v bajtech.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-113">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5dbe-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a5dbe-114">Return Value</span></span>  
 <span data-ttu-id="a5dbe-115">S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-115">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5dbe-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5dbe-116">See Also</span></span>  
 [<span data-ttu-id="a5dbe-117">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a5dbe-117">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
