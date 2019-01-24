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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a08695c4e5df6aaa63bedecf68b741302e5ddd8e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524936"
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="8efc9-102">ISymUnmanagedReader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8efc9-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="8efc9-103">Představuje modul pro načítání symbolů, který poskytuje přístup k dokumentům, metody a proměnných v úložišti symbolů.</span><span class="sxs-lookup"><span data-stu-id="8efc9-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="8efc9-104">Toto rozhraní rozšiřuje [isymunmanagedreader –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8efc9-104">This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8efc9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8efc9-105">Methods</span></span>  
  
|<span data-ttu-id="8efc9-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="8efc9-106">Method</span></span>|<span data-ttu-id="8efc9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8efc9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8efc9-108">GetMethodByVersionPreRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="8efc9-108">GetMethodByVersionPreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="8efc9-109">Získáte metodu čtečky symbolů daný token metody a číslo verze edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="8efc9-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="8efc9-110">GetMethodsInDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="8efc9-110">GetMethodsInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="8efc9-111">Získá každou metodu, která obsahuje informace o řádek v zadané dokumentu.</span><span class="sxs-lookup"><span data-stu-id="8efc9-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="8efc9-112">GetSymAttributePreRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="8efc9-112">GetSymAttributePreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="8efc9-113">Získá vlastní atribut na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="8efc9-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8efc9-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8efc9-114">Requirements</span></span>  
 <span data-ttu-id="8efc9-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8efc9-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8efc9-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8efc9-116">See also</span></span>
- [<span data-ttu-id="8efc9-117">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="8efc9-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="8efc9-118">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8efc9-118">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
