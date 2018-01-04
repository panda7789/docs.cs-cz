---
title: "ISymUnmanagedReader2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader2
helpviewer_keywords: ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 93f4b88d891d7b5c1d92006276a290841372aad7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="dc989-102">ISymUnmanagedReader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc989-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="dc989-103">Představuje čtečku symbol, který poskytuje přístup k dokumentům, metod a proměnné v rámci úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="dc989-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="dc989-104">Toto rozhraní rozšiřuje [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dc989-104">This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dc989-105">Metody</span><span class="sxs-lookup"><span data-stu-id="dc989-105">Methods</span></span>  
  
|<span data-ttu-id="dc989-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="dc989-106">Method</span></span>|<span data-ttu-id="dc989-107">Popis</span><span class="sxs-lookup"><span data-stu-id="dc989-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dc989-108">GetMethodByVersionPreRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="dc989-108">GetMethodByVersionPreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="dc989-109">Získání čtečky metodu symbol, zadaný token metoda a čísla verze upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="dc989-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="dc989-110">GetMethodsInDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="dc989-110">GetMethodsInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="dc989-111">Získá každých metoda, která obsahuje informace o řádku v zadané dokumentu.</span><span class="sxs-lookup"><span data-stu-id="dc989-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="dc989-112">GetSymAttributePreRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="dc989-112">GetSymAttributePreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="dc989-113">Získá vlastní atribut na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="dc989-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dc989-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc989-114">Requirements</span></span>  
 <span data-ttu-id="dc989-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="dc989-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc989-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc989-116">See Also</span></span>  
 [<span data-ttu-id="dc989-117">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="dc989-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="dc989-118">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc989-118">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
