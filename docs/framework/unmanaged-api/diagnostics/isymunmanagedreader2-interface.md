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
ms.openlocfilehash: 890053e1bf2e0648a41cca718e94edcf21c7e612
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165981"
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="71d55-102">ISymUnmanagedReader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="71d55-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="71d55-103">Představuje modul pro načítání symbolů, který poskytuje přístup k dokumentům, metody a proměnných v úložišti symbolů.</span><span class="sxs-lookup"><span data-stu-id="71d55-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="71d55-104">Toto rozhraní rozšiřuje [isymunmanagedreader –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="71d55-104">This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="71d55-105">Metody</span><span class="sxs-lookup"><span data-stu-id="71d55-105">Methods</span></span>  
  
|<span data-ttu-id="71d55-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="71d55-106">Method</span></span>|<span data-ttu-id="71d55-107">Popis</span><span class="sxs-lookup"><span data-stu-id="71d55-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="71d55-108">GetMethodByVersionPreRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="71d55-108">GetMethodByVersionPreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="71d55-109">Získáte metodu čtečky symbolů daný token metody a číslo verze edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="71d55-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="71d55-110">GetMethodsInDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="71d55-110">GetMethodsInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="71d55-111">Získá každou metodu, která obsahuje informace o řádek v zadané dokumentu.</span><span class="sxs-lookup"><span data-stu-id="71d55-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="71d55-112">GetSymAttributePreRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="71d55-112">GetSymAttributePreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="71d55-113">Získá vlastní atribut na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="71d55-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="71d55-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="71d55-114">Requirements</span></span>  
 <span data-ttu-id="71d55-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="71d55-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71d55-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71d55-116">See also</span></span>

- [<span data-ttu-id="71d55-117">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="71d55-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="71d55-118">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="71d55-118">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
