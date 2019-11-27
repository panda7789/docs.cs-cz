---
title: Rozhraní úložiště symbolů diagnostiky
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
ms.openlocfilehash: bdb691570a9a2bf7bd2bb21af500b06c10b0bc53
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448522"
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="ed423-102">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="ed423-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="ed423-103">Toto téma popisuje nespravovaná rozhraní, která umožňují kompilátoru generovat informace o symbolech pro použití v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="ed423-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ed423-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ed423-104">In This Section</span></span>  
 [<span data-ttu-id="ed423-105">IBindingDisplay – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-105">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 <span data-ttu-id="ed423-106">Poskytuje metody, které zobrazují aktuální informace o vazbě spuštěné aplikace.</span><span class="sxs-lookup"><span data-stu-id="ed423-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="ed423-107">IDebugAutoAttach – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-107">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 <span data-ttu-id="ed423-108">Definuje rozhraní pro automatické připojování ladicího programu spouštěného serverem.</span><span class="sxs-lookup"><span data-stu-id="ed423-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="ed423-109">INotifyConnection2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-109">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 <span data-ttu-id="ed423-110">Deklaruje metody pro registraci a zrušení registrace zdroje oznámení o připojení.</span><span class="sxs-lookup"><span data-stu-id="ed423-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="ed423-111">INotifySink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-111">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 <span data-ttu-id="ed423-112">Deklaruje metody pro oznámení jímky.</span><span class="sxs-lookup"><span data-stu-id="ed423-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="ed423-113">INotifySource2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 <span data-ttu-id="ed423-114">Deklaruje metodu pro nastavení filtrů oznámení.</span><span class="sxs-lookup"><span data-stu-id="ed423-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="ed423-115">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="ed423-116">Poskytuje informace o funkci upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="ed423-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="ed423-117">ISymUnmanagedAsyncMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-117">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="ed423-118">Toto rozhraní je doplňkem pro čtení [rozhraní ISymUnmanagedAsyncMethodPropertiesWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ed423-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="ed423-119">ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="ed423-120">Umožňuje definici nepovinné informace o asynchronní metodě na symbol metody.</span><span class="sxs-lookup"><span data-stu-id="ed423-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="ed423-121">Musí používat s otevřenou metodou (to znamená mezi voláním [metody OpenMethod –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)a [metodou CloseMethod –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span><span class="sxs-lookup"><span data-stu-id="ed423-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="ed423-122">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-122">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 <span data-ttu-id="ed423-123">Představuje pořadač symbolů pro nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="ed423-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="ed423-124">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-124">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="ed423-125">Představuje pořadač symbolů pro nespravovaný kód a rozšiřuje rozhraní `ISymUnmanagedBinder`.</span><span class="sxs-lookup"><span data-stu-id="ed423-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="ed423-126">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-126">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="ed423-127">Představuje pořadač symbolů pro nespravovaný kód a rozšiřuje rozhraní `ISymUnmanagedBinder`.</span><span class="sxs-lookup"><span data-stu-id="ed423-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="ed423-128">ISymUnmanagedConstant – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-128">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 <span data-ttu-id="ed423-129">Poskytuje přístup k nespravovaným konstantám.</span><span class="sxs-lookup"><span data-stu-id="ed423-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="ed423-130">ISymUnmanagedDispose – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-130">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 <span data-ttu-id="ed423-131">Likvidace nespravovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="ed423-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="ed423-132">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-132">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 <span data-ttu-id="ed423-133">Představuje dokument, na který odkazuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="ed423-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="ed423-134">ISymUnmanagedDocumentWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-134">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="ed423-135">Poskytuje metody pro zápis do dokumentu, na který odkazuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="ed423-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="ed423-136">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-136">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="ed423-137">Poskytuje metody pro funkci upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="ed423-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="ed423-138">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-138">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 <span data-ttu-id="ed423-139">Představuje metodu v úložišti symbolů.</span><span class="sxs-lookup"><span data-stu-id="ed423-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="ed423-140">ISymUnmanagedNamespace – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-140">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 <span data-ttu-id="ed423-141">Představuje obor názvů.</span><span class="sxs-lookup"><span data-stu-id="ed423-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="ed423-142">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-142">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 <span data-ttu-id="ed423-143">Představuje čtečku symbolů, která poskytuje přístup k dokumentům, metodám a proměnným v rámci úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="ed423-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="ed423-144">ISymUnmanagedReader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-144">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 <span data-ttu-id="ed423-145">Získá metodu čtečky symbolů pro token metody a číslo verze pro úpravy a kopírování.</span><span class="sxs-lookup"><span data-stu-id="ed423-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="ed423-146">ISymUnmanagedReaderSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="ed423-147">Poskytuje metody, které získávají informace o hledání symbolů.</span><span class="sxs-lookup"><span data-stu-id="ed423-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="ed423-148">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-148">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 <span data-ttu-id="ed423-149">Představuje lexikální obor v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="ed423-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="ed423-150">ISymUnmanagedScope2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-150">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 <span data-ttu-id="ed423-151">Představuje lexikální obor v rámci metody a rozšiřuje rozhraní `ISymUnmanagedScope` s metodami, které získávají informace o konstantách definovaných v rámci oboru.</span><span class="sxs-lookup"><span data-stu-id="ed423-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="ed423-152">ISymUnmanagedSourceServerModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-152">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="ed423-153">Poskytuje data zdrojového serveru pro modul.</span><span class="sxs-lookup"><span data-stu-id="ed423-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="ed423-154">ISymUnmanagedSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="ed423-155">Poskytuje metody, které získávají informace o cestě pro hledání.</span><span class="sxs-lookup"><span data-stu-id="ed423-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="ed423-156">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-156">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 <span data-ttu-id="ed423-157">Představuje proměnnou, jako je například parametr, místní proměnná nebo pole.</span><span class="sxs-lookup"><span data-stu-id="ed423-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="ed423-158">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-158">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 <span data-ttu-id="ed423-159">Představuje zapisovač symbolů a poskytuje metody pro definování dokumentů, sekvenčních bodů, lexikálních oborů a proměnných.</span><span class="sxs-lookup"><span data-stu-id="ed423-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="ed423-160">ISymUnmanagedWriter2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-160">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="ed423-161">Představuje zapisovač symbolů a poskytuje metody pro definování dokumentů, sekvenčních bodů, lexikálních oborů a proměnných.</span><span class="sxs-lookup"><span data-stu-id="ed423-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="ed423-162">Rozšiřuje rozhraní `ISymUnmanagedWriter`.</span><span class="sxs-lookup"><span data-stu-id="ed423-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="ed423-163">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-163">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="ed423-164">Představuje zapisovač symbolů a poskytuje metody pro definování dokumentů, sekvenčních bodů, lexikálních oborů a proměnných.</span><span class="sxs-lookup"><span data-stu-id="ed423-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="ed423-165">Rozšiřuje rozhraní `ISymUnmanagedWriter`.</span><span class="sxs-lookup"><span data-stu-id="ed423-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="ed423-166">ISymUnmanagedWriter4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-166">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="ed423-167">Rozhraní Isymunmanagedwriter4 –</span><span class="sxs-lookup"><span data-stu-id="ed423-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="ed423-168">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed423-168">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="ed423-169">Rozhraní ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="ed423-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ed423-170">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ed423-170">Related Sections</span></span>  
 [<span data-ttu-id="ed423-171">Výčty pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="ed423-171">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="ed423-172">Struktury pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="ed423-172">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="ed423-173">Ladění</span><span class="sxs-lookup"><span data-stu-id="ed423-173">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
