---
title: "ISymUnmanagedReader – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedReader
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader
helpviewer_keywords:
- ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9e8daea11292cb37deb8e956e6a666c14579fbfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="e013c-102">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e013c-102">ISymUnmanagedReader Interface</span></span>
<span data-ttu-id="e013c-103">Představuje čtečku symbol, který poskytuje přístup k dokumentům, metod a proměnné v rámci úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="e013c-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e013c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e013c-104">Methods</span></span>  
  
|<span data-ttu-id="e013c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e013c-105">Method</span></span>|<span data-ttu-id="e013c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e013c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e013c-107">GetDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="e013c-107">GetDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="e013c-108">Vyhledá dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e013c-108">Finds a document.</span></span>|  
|[<span data-ttu-id="e013c-109">GetDocuments – metoda</span><span class="sxs-lookup"><span data-stu-id="e013c-109">GetDocuments Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="e013c-110">Vrátí pole všech dokumentů, které jsou definované v úložišti symbol.</span><span class="sxs-lookup"><span data-stu-id="e013c-110">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="e013c-111">GetDocumentVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="e013c-111">GetDocumentVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="e013c-112">Získá určenou verzi zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="e013c-112">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="e013c-113">GetGlobalVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="e013c-113">GetGlobalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="e013c-114">Vrátí všechny globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="e013c-114">Returns all global variables.</span></span>|  
|[<span data-ttu-id="e013c-115">GetMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="e013c-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="e013c-116">Získá metody čtečky symbol, zadaný token metoda.</span><span class="sxs-lookup"><span data-stu-id="e013c-116">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="e013c-117">GetMethodByVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="e013c-117">GetMethodByVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="e013c-118">Získá metody čtečky symbol, zadaný token metoda a čísla verze úpravy a kopie.</span><span class="sxs-lookup"><span data-stu-id="e013c-118">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="e013c-119">GetMethodFromDocumentPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="e013c-119">GetMethodFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="e013c-120">Vrátí metodu, která obsahuje bod přerušení na dané pozici v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e013c-120">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="e013c-121">GetMethodsFromDocumentPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="e013c-121">GetMethodsFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="e013c-122">Vrátí pole metod, z nichž každý obsahuje zarážek na dané pozici v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e013c-122">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="e013c-123">GetMethodVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="e013c-123">GetMethodVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="e013c-124">Získá verzi metoda.</span><span class="sxs-lookup"><span data-stu-id="e013c-124">Gets the method version.</span></span>|  
|[<span data-ttu-id="e013c-125">GetNamespaces – metoda</span><span class="sxs-lookup"><span data-stu-id="e013c-125">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="e013c-126">Získá oborů názvů definovaných v globálním oboru v rámci úložiště tento symbol.</span><span class="sxs-lookup"><span data-stu-id="e013c-126">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="e013c-127">GetSymAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="e013c-127">GetSymAttribute Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="e013c-128">Získá vlastní atribut na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="e013c-128">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="e013c-129">GetSymbolStoreFileName – metoda</span><span class="sxs-lookup"><span data-stu-id="e013c-129">GetSymbolStoreFileName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="e013c-130">Obsahuje název souboru na disku úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="e013c-130">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="e013c-131">GetUserEntryPoint – metoda</span><span class="sxs-lookup"><span data-stu-id="e013c-131">GetUserEntryPoint Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="e013c-132">Vrátí metodu, která byla zadána jako vstupní bod uživatele modulu, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="e013c-132">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="e013c-133">GetVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="e013c-133">GetVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="e013c-134">Vrátí proměnnou jiné než místní, daného jeho nadřazený a název.</span><span class="sxs-lookup"><span data-stu-id="e013c-134">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="e013c-135">Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="e013c-135">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|<span data-ttu-id="e013c-136">Inicializuje čtečky symbol s rozhraním program pro import metadat, které bude tato čtečky spojený s, spolu s názvem souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="e013c-136">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="e013c-137">ReplaceSymbolStore – metoda</span><span class="sxs-lookup"><span data-stu-id="e013c-137">ReplaceSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="e013c-138">Nahradí existující úložiště symbolů s úložištěm symbol delta.</span><span class="sxs-lookup"><span data-stu-id="e013c-138">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="e013c-139">UpdateSymbolStore – metoda</span><span class="sxs-lookup"><span data-stu-id="e013c-139">UpdateSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="e013c-140">Aktualizuje existující úložiště symbolů s úložištěm symbol delta.</span><span class="sxs-lookup"><span data-stu-id="e013c-140">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e013c-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e013c-141">Requirements</span></span>  
 <span data-ttu-id="e013c-142">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e013c-142">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e013c-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="e013c-143">See Also</span></span>  
 [<span data-ttu-id="e013c-144">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="e013c-144">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="e013c-145">ISymUnmanagedReader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e013c-145">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
