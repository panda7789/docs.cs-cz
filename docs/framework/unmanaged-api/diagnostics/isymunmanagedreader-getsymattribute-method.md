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
ms.openlocfilehash: b7e2814e56765037b69c6ef7ca0ba610dd7d3c95
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614926"
---
# <a name="isymunmanagedreadergetsymattribute-method"></a><span data-ttu-id="9599c-102">ISymUnmanagedReader::GetSymAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="9599c-102">ISymUnmanagedReader::GetSymAttribute Method</span></span>
<span data-ttu-id="9599c-103">Získá vlastní atribut založený na jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="9599c-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="9599c-104">Na rozdíl od vlastních atributů metadat jsou tyto vlastní atributy uchovávány v úložišti symbolů.</span><span class="sxs-lookup"><span data-stu-id="9599c-104">Unlike metadata custom attributes, these custom attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9599c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9599c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9599c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9599c-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="9599c-107">pro Token metadat pro objekt, pro který je požadován atribut.</span><span class="sxs-lookup"><span data-stu-id="9599c-107">[in] The metadata token for the object for which the attribute is requested.</span></span>  
  
 `name`  
 <span data-ttu-id="9599c-108">pro Ukazatel na proměnnou, která označuje atribut, který má být načten.</span><span class="sxs-lookup"><span data-stu-id="9599c-108">[in] A pointer to the variable that indicates the attribute to retrieve.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="9599c-109">pro Velikost `buffer` pole.</span><span class="sxs-lookup"><span data-stu-id="9599c-109">[in] The size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="9599c-110">mimo Ukazatel na proměnnou, která přijímá délku dat atributu.</span><span class="sxs-lookup"><span data-stu-id="9599c-110">[out] A pointer to the variable that receives the length of the attribute data.</span></span>  
  
 `buffer`  
 <span data-ttu-id="9599c-111">mimo Ukazatel na proměnnou, která přijímá data atributu.</span><span class="sxs-lookup"><span data-stu-id="9599c-111">[out] A pointer to the variable that receives the attribute data.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9599c-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9599c-112">Return Value</span></span>  
 <span data-ttu-id="9599c-113">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="9599c-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9599c-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9599c-114">Requirements</span></span>  
 <span data-ttu-id="9599c-115">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="9599c-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9599c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9599c-116">See also</span></span>

- [<span data-ttu-id="9599c-117">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9599c-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
