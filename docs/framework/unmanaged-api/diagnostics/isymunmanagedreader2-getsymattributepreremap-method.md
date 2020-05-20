---
title: ISymUnmanagedReader2::GetSymAttributePreRemap – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetSymAttributePreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type:
- apiref
ms.openlocfilehash: e6248aba1c41b2815f2806942d419da869ed94b4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614913"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a><span data-ttu-id="3b1ff-102">ISymUnmanagedReader2::GetSymAttributePreRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="3b1ff-102">ISymUnmanagedReader2::GetSymAttributePreRemap Method</span></span>
<span data-ttu-id="3b1ff-103">Získá vlastní atribut založený na jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="3b1ff-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="3b1ff-104">Na rozdíl od vlastních atributů metadat jsou tyto atributy uchovávány v úložišti symbolů.</span><span class="sxs-lookup"><span data-stu-id="3b1ff-104">Unlike metadata custom attributes, these attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b1ff-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b1ff-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b1ff-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3b1ff-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="3b1ff-107">pro Token metadat nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="3b1ff-107">[in] The metadata token of the parent.</span></span>  
  
 `name`  
 <span data-ttu-id="3b1ff-108">pro Ukazatel na `WCHAR` , který obsahuje název.</span><span class="sxs-lookup"><span data-stu-id="3b1ff-108">[in] A pointer to a `WCHAR` that contains the name.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="3b1ff-109">pro `ULONG32`Který označuje velikost `buffer` pole.</span><span class="sxs-lookup"><span data-stu-id="3b1ff-109">[in] A `ULONG32` that indicates the size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="3b1ff-110">mimo Ukazatel na `ULONG32` , který přijímá velikost vyrovnávací paměti vyžadované k omezení bajtů atributů.</span><span class="sxs-lookup"><span data-stu-id="3b1ff-110">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span></span>  
  
 `buffer`  
 <span data-ttu-id="3b1ff-111">mimo Ukazatel na vyrovnávací paměť, která přijímá bajty atributů.</span><span class="sxs-lookup"><span data-stu-id="3b1ff-111">[out] A pointer to the buffer that receives the attribute bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b1ff-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3b1ff-112">Return Value</span></span>  
 <span data-ttu-id="3b1ff-113">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="3b1ff-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b1ff-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3b1ff-114">Requirements</span></span>  
 <span data-ttu-id="3b1ff-115">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3b1ff-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b1ff-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b1ff-116">See also</span></span>

- [<span data-ttu-id="3b1ff-117">ISymUnmanagedReader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3b1ff-117">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
