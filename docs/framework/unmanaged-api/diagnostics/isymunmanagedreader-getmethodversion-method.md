---
title: ISymUnmanagedReader::GetMethodVersion – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodVersion
helpviewer_keywords:
- GetMethodVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodVersion method [.NET Framework debugging]
ms.assetid: d6f9ac84-302a-4f5e-b990-e76f4269fceb
topic_type:
- apiref
ms.openlocfilehash: 8ee4c1bffccb44d15fa53eb3d4d6c0fcdc3e7697
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614965"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="ba51f-102">ISymUnmanagedReader::GetMethodVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="ba51f-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>
<span data-ttu-id="ba51f-103">Získá verzi metody.</span><span class="sxs-lookup"><span data-stu-id="ba51f-103">Gets the method version.</span></span> <span data-ttu-id="ba51f-104">Verze metody začíná na 1 a při každém překompilování metody se zvýší.</span><span class="sxs-lookup"><span data-stu-id="ba51f-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="ba51f-105">Opětovná kompilace může probíhat beze změn v metodě.</span><span class="sxs-lookup"><span data-stu-id="ba51f-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba51f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba51f-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba51f-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="ba51f-107">Parameters</span></span>  
 `pMethod`  
 <span data-ttu-id="ba51f-108">pro Metoda, pro kterou se má získat verze</span><span class="sxs-lookup"><span data-stu-id="ba51f-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="ba51f-109">mimo Ukazatel na proměnnou, která přijímá verzi metody.</span><span class="sxs-lookup"><span data-stu-id="ba51f-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba51f-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ba51f-110">Return Value</span></span>  
 <span data-ttu-id="ba51f-111">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="ba51f-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba51f-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ba51f-112">Requirements</span></span>  
 <span data-ttu-id="ba51f-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ba51f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba51f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba51f-114">See also</span></span>

- [<span data-ttu-id="ba51f-115">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba51f-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
