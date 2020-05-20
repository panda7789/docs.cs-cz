---
title: ISymUnmanagedReader – rozhraní
ms.date: 03/30/2017
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
ms.openlocfilehash: b372021fcda39d9973d96a9c39e93e38617887a6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615459"
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="bb272-102">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb272-102">ISymUnmanagedReader Interface</span></span>
<span data-ttu-id="bb272-103">Představuje čtečku symbolů, která poskytuje přístup k dokumentům, metodám a proměnným v rámci úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="bb272-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bb272-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bb272-104">Methods</span></span>  
  
|<span data-ttu-id="bb272-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bb272-105">Method</span></span>|<span data-ttu-id="bb272-106">Popis</span><span class="sxs-lookup"><span data-stu-id="bb272-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bb272-107">GetDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="bb272-107">GetDocument Method</span></span>](isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="bb272-108">Najde dokument.</span><span class="sxs-lookup"><span data-stu-id="bb272-108">Finds a document.</span></span>|  
|[<span data-ttu-id="bb272-109">GetDocuments – metoda</span><span class="sxs-lookup"><span data-stu-id="bb272-109">GetDocuments Method</span></span>](isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="bb272-110">Vrátí pole všech dokumentů definovaných v úložišti symbolů.</span><span class="sxs-lookup"><span data-stu-id="bb272-110">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="bb272-111">GetDocumentVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="bb272-111">GetDocumentVersion Method</span></span>](isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="bb272-112">Načte zadanou verzi zadaného dokumentu.</span><span class="sxs-lookup"><span data-stu-id="bb272-112">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="bb272-113">GetGlobalVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="bb272-113">GetGlobalVariables Method</span></span>](isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="bb272-114">Vrátí všechny globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="bb272-114">Returns all global variables.</span></span>|  
|[<span data-ttu-id="bb272-115">GetMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="bb272-115">GetMethod Method</span></span>](isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="bb272-116">Získá metodu čtečky symbolů s ohledem na token metody.</span><span class="sxs-lookup"><span data-stu-id="bb272-116">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="bb272-117">GetMethodByVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="bb272-117">GetMethodByVersion Method</span></span>](isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="bb272-118">Získá metodu čtečky symbolů s ohledem na token metody a číslo verze pro úpravy a kopírování.</span><span class="sxs-lookup"><span data-stu-id="bb272-118">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="bb272-119">GetMethodFromDocumentPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="bb272-119">GetMethodFromDocumentPosition Method</span></span>](isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="bb272-120">Vrátí metodu, která obsahuje zarážku na dané pozici v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="bb272-120">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="bb272-121">GetMethodsFromDocumentPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="bb272-121">GetMethodsFromDocumentPosition Method</span></span>](isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="bb272-122">Vrátí pole metod, z nichž každý obsahuje zarážku na dané pozici v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="bb272-122">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="bb272-123">GetMethodVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="bb272-123">GetMethodVersion Method</span></span>](isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="bb272-124">Získá verzi metody.</span><span class="sxs-lookup"><span data-stu-id="bb272-124">Gets the method version.</span></span>|  
|[<span data-ttu-id="bb272-125">GetNamespaces – metoda</span><span class="sxs-lookup"><span data-stu-id="bb272-125">GetNamespaces Method</span></span>](isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="bb272-126">Načte obory názvů definované v globálním oboru v rámci tohoto úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="bb272-126">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="bb272-127">GetSymAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="bb272-127">GetSymAttribute Method</span></span>](isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="bb272-128">Získá vlastní atribut založený na jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="bb272-128">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="bb272-129">GetSymbolStoreFileName – metoda</span><span class="sxs-lookup"><span data-stu-id="bb272-129">GetSymbolStoreFileName Method</span></span>](isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="bb272-130">Poskytuje název souboru na disku pro úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="bb272-130">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="bb272-131">GetUserEntryPoint – metoda</span><span class="sxs-lookup"><span data-stu-id="bb272-131">GetUserEntryPoint Method</span></span>](isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="bb272-132">Vrátí metodu, která byla zadána jako vstupní bod uživatele pro modul, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="bb272-132">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="bb272-133">GetVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="bb272-133">GetVariables Method</span></span>](isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="bb272-134">Vrátí nemístní proměnnou, která má zadaný nadřazený prvek a název.</span><span class="sxs-lookup"><span data-stu-id="bb272-134">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="bb272-135">Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="bb272-135">Initialize Method</span></span>](isymunmanagedreader-initialize-method.md)|<span data-ttu-id="bb272-136">Inicializuje čtečku symbolů pomocí rozhraní pro import metadat, ke kterému bude tento čtenář přidružen, společně s názvem souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="bb272-136">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="bb272-137">ReplaceSymbolStore – metoda</span><span class="sxs-lookup"><span data-stu-id="bb272-137">ReplaceSymbolStore Method</span></span>](isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="bb272-138">Nahradí existující úložiště symbolů rozdílovým úložištěm symbolů.</span><span class="sxs-lookup"><span data-stu-id="bb272-138">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="bb272-139">UpdateSymbolStore – metoda</span><span class="sxs-lookup"><span data-stu-id="bb272-139">UpdateSymbolStore Method</span></span>](isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="bb272-140">Aktualizuje existující úložiště symbolů pomocí rozdílového úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="bb272-140">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bb272-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb272-141">Requirements</span></span>  
 <span data-ttu-id="bb272-142">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="bb272-142">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb272-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb272-143">See also</span></span>

- [<span data-ttu-id="bb272-144">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="bb272-144">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="bb272-145">ISymUnmanagedReader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb272-145">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
