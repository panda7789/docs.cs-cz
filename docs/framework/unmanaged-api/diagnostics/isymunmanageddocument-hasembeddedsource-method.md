---
title: ISymUnmanagedDocument::HasEmbeddedSource – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.HasEmbeddedSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::HasEmbeddedSource
helpviewer_keywords:
- HasEmbeddedSource method [.NET Framework debugging]
- ISymUnmanagedDocument::HasEmbeddedSource method [.NET Framework debugging]
ms.assetid: 385fc4d3-365c-4645-b7b0-6c4c5344b79f
topic_type:
- apiref
ms.openlocfilehash: d654f6d57bd784063fc7f87dd9767bdc27ad2776
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615576"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="8ab41-102">ISymUnmanagedDocument::HasEmbeddedSource – metoda</span><span class="sxs-lookup"><span data-stu-id="8ab41-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="8ab41-103">Vrátí, `true` zda má dokument ve symbolech ladění zdroj vložený. v opačném případě vrátí `false` .</span><span class="sxs-lookup"><span data-stu-id="8ab41-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ab41-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ab41-104">Syntax</span></span>  
  
```cpp  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ab41-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ab41-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="8ab41-106">mimo Ukazatel na proměnnou, která označuje, zda má dokument ve symbolech ladění zdroj vložený.</span><span class="sxs-lookup"><span data-stu-id="8ab41-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ab41-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8ab41-107">Return Value</span></span>  
 <span data-ttu-id="8ab41-108">S_OK, zda je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="8ab41-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ab41-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ab41-109">See also</span></span>

- [<span data-ttu-id="8ab41-110">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ab41-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
