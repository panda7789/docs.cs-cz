---
title: ISymUnmanagedDocument::GetURL – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetURL
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a93ef073d4dd2eaf58c057d4cdf25fa39082e14
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706323"
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="b08f6-102">ISymUnmanagedDocument::GetURL – metoda</span><span class="sxs-lookup"><span data-stu-id="b08f6-102">ISymUnmanagedDocument::GetURL Method</span></span>
<span data-ttu-id="b08f6-103">Vrátí adresu uniform resource locator (URL) pro tento dokument.</span><span class="sxs-lookup"><span data-stu-id="b08f6-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b08f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b08f6-104">Syntax</span></span>  
  
```  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b08f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b08f6-105">Parameters</span></span>  
 `cchUrl`  
 <span data-ttu-id="b08f6-106">[in] Velikost ve znacích, nástroje `szURL` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="b08f6-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="b08f6-107">[out] Ukazovat na proměnnou, která bude přijímat velikost adresy URL, včetně ukončení hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b08f6-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="b08f6-108">[out] Vyrovnávací paměti, který obsahuje adresu URL.</span><span class="sxs-lookup"><span data-stu-id="b08f6-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b08f6-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b08f6-109">Return Value</span></span>  
 <span data-ttu-id="b08f6-110">Pokud metoda uspěje; S_OK v opačném případě chybový kód.</span><span class="sxs-lookup"><span data-stu-id="b08f6-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b08f6-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b08f6-111">See also</span></span>
- [<span data-ttu-id="b08f6-112">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b08f6-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
