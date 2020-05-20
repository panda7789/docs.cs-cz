---
title: ISymUnmanagedReader2 – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2
helpviewer_keywords:
- ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type:
- apiref
ms.openlocfilehash: d4c5ff46d37b1292059b18920abd8042c18bbf31
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615394"
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="7ede2-102">ISymUnmanagedReader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ede2-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="7ede2-103">Představuje čtečku symbolů, která poskytuje přístup k dokumentům, metodám a proměnným v rámci úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="7ede2-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="7ede2-104">Toto rozhraní rozšiřuje rozhraní [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="7ede2-104">This interface extends the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ede2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7ede2-105">Methods</span></span>  
  
|<span data-ttu-id="7ede2-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="7ede2-106">Method</span></span>|<span data-ttu-id="7ede2-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7ede2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7ede2-108">GetMethodByVersionPreRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="7ede2-108">GetMethodByVersionPreRemap Method</span></span>](isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="7ede2-109">Získejte metodu čtečky symbolů s ohledem na token metody a číslo verze Edit-and-Continue.</span><span class="sxs-lookup"><span data-stu-id="7ede2-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="7ede2-110">GetMethodsInDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="7ede2-110">GetMethodsInDocument Method</span></span>](isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="7ede2-111">Načte každou metodu, která obsahuje informace o řádku v zadaném dokumentu.</span><span class="sxs-lookup"><span data-stu-id="7ede2-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="7ede2-112">GetSymAttributePreRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="7ede2-112">GetSymAttributePreRemap Method</span></span>](isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="7ede2-113">Získá vlastní atribut založený na jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="7ede2-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7ede2-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ede2-114">Requirements</span></span>  
 <span data-ttu-id="7ede2-115">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="7ede2-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ede2-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ede2-116">See also</span></span>

- [<span data-ttu-id="7ede2-117">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="7ede2-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="7ede2-118">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ede2-118">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
