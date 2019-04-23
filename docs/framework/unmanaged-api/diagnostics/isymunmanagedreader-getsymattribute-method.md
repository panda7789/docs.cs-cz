---
title: ISymUnmanagedReader::GetSymAttribute – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymAttribute
helpviewer_keywords:
- GetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymAttribute method [.NET Framework debugging]
ms.assetid: c675ce7e-76e7-45ff-8273-3b6489a2767c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 89831261c5da156343cb098ace715495ddafccaf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086088"
---
# <a name="isymunmanagedreadergetsymattribute-method"></a><span data-ttu-id="31ef0-102">ISymUnmanagedReader::GetSymAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="31ef0-102">ISymUnmanagedReader::GetSymAttribute Method</span></span>
<span data-ttu-id="31ef0-103">Získá vlastní atribut na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="31ef0-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="31ef0-104">Na rozdíl od vlastních atributů metadat jsou tyto vlastní atributy uložené v úložišti symbolů.</span><span class="sxs-lookup"><span data-stu-id="31ef0-104">Unlike metadata custom attributes, these custom attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31ef0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31ef0-105">Syntax</span></span>  
  
```  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31ef0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="31ef0-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="31ef0-107">[in] Token metadat pro objekt, pro který je požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="31ef0-107">[in] The metadata token for the object for which the attribute is requested.</span></span>  
  
 `name`  
 <span data-ttu-id="31ef0-108">[in] Ukazatel na proměnnou, která určuje atribut, který chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="31ef0-108">[in] A pointer to the variable that indicates the attribute to retrieve.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="31ef0-109">[in] Velikost `buffer` pole.</span><span class="sxs-lookup"><span data-stu-id="31ef0-109">[in] The size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="31ef0-110">[out] Ukazatel na proměnnou, která přijímá délka dat atribut.</span><span class="sxs-lookup"><span data-stu-id="31ef0-110">[out] A pointer to the variable that receives the length of the attribute data.</span></span>  
  
 `buffer`  
 <span data-ttu-id="31ef0-111">[out] Ukazatel na proměnnou, která přijímá data atributu.</span><span class="sxs-lookup"><span data-stu-id="31ef0-111">[out] A pointer to the variable that receives the attribute data.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31ef0-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="31ef0-112">Return Value</span></span>  
 <span data-ttu-id="31ef0-113">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="31ef0-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31ef0-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="31ef0-114">Requirements</span></span>  
 <span data-ttu-id="31ef0-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="31ef0-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31ef0-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31ef0-116">See also</span></span>

- [<span data-ttu-id="31ef0-117">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="31ef0-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
