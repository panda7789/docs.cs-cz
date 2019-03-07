---
title: ISymUnmanagedDocument::GetCheckSum – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 80cda4c31ca78e0350639df809ec1e9f1dcbbaea
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498247"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="85c33-102">ISymUnmanagedDocument::GetCheckSum – metoda</span><span class="sxs-lookup"><span data-stu-id="85c33-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="85c33-103">Získá kontrolní součet.</span><span class="sxs-lookup"><span data-stu-id="85c33-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85c33-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85c33-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85c33-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="85c33-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="85c33-106">[in] Délka vyrovnávací paměti poskytované `data` parametr</span><span class="sxs-lookup"><span data-stu-id="85c33-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="85c33-107">[out] Velikost a délce kontrolní součet v bajtech.</span><span class="sxs-lookup"><span data-stu-id="85c33-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="85c33-108">[out] Vyrovnávací paměť, která přijímá kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="85c33-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85c33-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="85c33-109">Return Value</span></span>  
 <span data-ttu-id="85c33-110">Pokud metoda uspěje; S_OK v opačném případě chybový kód.</span><span class="sxs-lookup"><span data-stu-id="85c33-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85c33-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85c33-111">See also</span></span>
- [<span data-ttu-id="85c33-112">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85c33-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
