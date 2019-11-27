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
ms.openlocfilehash: 7f04b5c100f1fd9c44e671b883fe469b16d33fa6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440147"
---
# <a name="isymunmanagedreadergetsymattribute-method"></a><span data-ttu-id="a63e5-102">ISymUnmanagedReader::GetSymAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="a63e5-102">ISymUnmanagedReader::GetSymAttribute Method</span></span>
<span data-ttu-id="a63e5-103">Získá vlastní atribut založený na jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="a63e5-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="a63e5-104">Na rozdíl od vlastních atributů metadat jsou tyto vlastní atributy uchovávány v úložišti symbolů.</span><span class="sxs-lookup"><span data-stu-id="a63e5-104">Unlike metadata custom attributes, these custom attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a63e5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a63e5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a63e5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a63e5-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="a63e5-107">pro Token metadat pro objekt, pro který je požadován atribut.</span><span class="sxs-lookup"><span data-stu-id="a63e5-107">[in] The metadata token for the object for which the attribute is requested.</span></span>  
  
 `name`  
 <span data-ttu-id="a63e5-108">pro Ukazatel na proměnnou, která označuje atribut, který má být načten.</span><span class="sxs-lookup"><span data-stu-id="a63e5-108">[in] A pointer to the variable that indicates the attribute to retrieve.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="a63e5-109">pro Velikost pole `buffer`.</span><span class="sxs-lookup"><span data-stu-id="a63e5-109">[in] The size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="a63e5-110">mimo Ukazatel na proměnnou, která přijímá délku dat atributu.</span><span class="sxs-lookup"><span data-stu-id="a63e5-110">[out] A pointer to the variable that receives the length of the attribute data.</span></span>  
  
 `buffer`  
 <span data-ttu-id="a63e5-111">mimo Ukazatel na proměnnou, která přijímá data atributu.</span><span class="sxs-lookup"><span data-stu-id="a63e5-111">[out] A pointer to the variable that receives the attribute data.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a63e5-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a63e5-112">Return Value</span></span>  
 <span data-ttu-id="a63e5-113">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="a63e5-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a63e5-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a63e5-114">Requirements</span></span>  
 <span data-ttu-id="a63e5-115">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a63e5-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a63e5-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a63e5-116">See also</span></span>

- [<span data-ttu-id="a63e5-117">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a63e5-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
