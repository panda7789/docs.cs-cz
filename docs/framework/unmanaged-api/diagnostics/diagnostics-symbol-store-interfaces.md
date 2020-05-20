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
ms.openlocfilehash: 044ed5e08a85442c5a73c123cf51529d2fd3f1fc
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442173"
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="0a0f4-102">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="0a0f4-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="0a0f4-103">Toto téma popisuje nespravovaná rozhraní, která umožňují kompilátoru generovat informace o symbolech pro použití v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0a0f4-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0a0f4-104">In This Section</span></span>  
 [<span data-ttu-id="0a0f4-105">IBindingDisplay – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-105">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)  
 <span data-ttu-id="0a0f4-106">Poskytuje metody, které zobrazují aktuální informace o vazbě spuštěné aplikace.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="0a0f4-107">IDebugAutoAttach – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-107">IDebugAutoAttach Interface</span></span>](idebugautoattach-interface.md)  
 <span data-ttu-id="0a0f4-108">Definuje rozhraní pro automatické připojování ladicího programu spouštěného serverem.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="0a0f4-109">INotifyConnection2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-109">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)  
 <span data-ttu-id="0a0f4-110">Deklaruje metody pro registraci a zrušení registrace zdroje oznámení o připojení.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="0a0f4-111">INotifySink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-111">INotifySink2 Interface</span></span>](inotifysink2-interface.md)  
 <span data-ttu-id="0a0f4-112">Deklaruje metody pro oznámení jímky.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="0a0f4-113">INotifySource2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-113">INotifySource2 Interface</span></span>](inotifysource2-interface.md)  
 <span data-ttu-id="0a0f4-114">Deklaruje metodu pro nastavení filtrů oznámení.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="0a0f4-115">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-115">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="0a0f4-116">Poskytuje informace o funkci upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="0a0f4-117">ISymUnmanagedAsyncMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-117">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="0a0f4-118">Toto rozhraní je doplňkem pro čtení [rozhraní ISymUnmanagedAsyncMethodPropertiesWriter](isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="0a0f4-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="0a0f4-119">ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="0a0f4-120">Umožňuje definici nepovinné informace o asynchronní metodě na symbol metody.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="0a0f4-121">Musí používat s otevřenou metodou (to znamená mezi voláním [metody OpenMethod –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)a [metodou CloseMethod –](isymunmanagedwriter-closemethod-method.md)).</span><span class="sxs-lookup"><span data-stu-id="0a0f4-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="0a0f4-122">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-122">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)  
 <span data-ttu-id="0a0f4-123">Představuje pořadač symbolů pro nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="0a0f4-124">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-124">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="0a0f4-125">Představuje pořadač symbolů pro nespravovaný kód a rozšiřuje `ISymUnmanagedBinder` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="0a0f4-126">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-126">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="0a0f4-127">Představuje pořadač symbolů pro nespravovaný kód a rozšiřuje `ISymUnmanagedBinder` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="0a0f4-128">ISymUnmanagedConstant – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-128">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)  
 <span data-ttu-id="0a0f4-129">Poskytuje přístup k nespravovaným konstantám.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="0a0f4-130">ISymUnmanagedDispose – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-130">ISymUnmanagedDispose Interface</span></span>](isymunmanageddispose-interface.md)  
 <span data-ttu-id="0a0f4-131">Likvidace nespravovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="0a0f4-132">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-132">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)  
 <span data-ttu-id="0a0f4-133">Představuje dokument, na který odkazuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="0a0f4-134">ISymUnmanagedDocumentWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-134">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="0a0f4-135">Poskytuje metody pro zápis do dokumentu, na který odkazuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="0a0f4-136">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-136">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="0a0f4-137">Poskytuje metody pro funkci upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="0a0f4-138">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-138">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)  
 <span data-ttu-id="0a0f4-139">Představuje metodu v úložišti symbolů.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="0a0f4-140">ISymUnmanagedNamespace – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-140">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)  
 <span data-ttu-id="0a0f4-141">Představuje obor názvů.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="0a0f4-142">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-142">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)  
 <span data-ttu-id="0a0f4-143">Představuje čtečku symbolů, která poskytuje přístup k dokumentům, metodám a proměnným v rámci úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="0a0f4-144">ISymUnmanagedReader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-144">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)  
 <span data-ttu-id="0a0f4-145">Získá metodu čtečky symbolů pro token metody a číslo verze pro úpravy a kopírování.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="0a0f4-146">ISymUnmanagedReaderSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="0a0f4-147">Poskytuje metody, které získávají informace o hledání symbolů.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="0a0f4-148">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-148">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)  
 <span data-ttu-id="0a0f4-149">Představuje lexikální obor v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="0a0f4-150">ISymUnmanagedScope2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-150">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)  
 <span data-ttu-id="0a0f4-151">Představuje lexikální obor v rámci metody a rozšiřuje `ISymUnmanagedScope` rozhraní o metody, které získávají informace o konstantách definovaných v rámci oboru.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="0a0f4-152">ISymUnmanagedSourceServerModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-152">ISymUnmanagedSourceServerModule Interface</span></span>](isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="0a0f4-153">Poskytuje data zdrojového serveru pro modul.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="0a0f4-154">ISymUnmanagedSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="0a0f4-155">Poskytuje metody, které získávají informace o cestě pro hledání.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="0a0f4-156">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-156">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)  
 <span data-ttu-id="0a0f4-157">Představuje proměnnou, jako je například parametr, místní proměnná nebo pole.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="0a0f4-158">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-158">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)  
 <span data-ttu-id="0a0f4-159">Představuje zapisovač symbolů a poskytuje metody pro definování dokumentů, sekvenčních bodů, lexikálních oborů a proměnných.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="0a0f4-160">ISymUnmanagedWriter2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-160">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="0a0f4-161">Představuje zapisovač symbolů a poskytuje metody pro definování dokumentů, sekvenčních bodů, lexikálních oborů a proměnných.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="0a0f4-162">Rozšiřuje `ISymUnmanagedWriter` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="0a0f4-163">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-163">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="0a0f4-164">Představuje zapisovač symbolů a poskytuje metody pro definování dokumentů, sekvenčních bodů, lexikálních oborů a proměnných.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="0a0f4-165">Rozšiřuje `ISymUnmanagedWriter` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0a0f4-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="0a0f4-166">ISymUnmanagedWriter4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-166">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="0a0f4-167">Rozhraní Isymunmanagedwriter4 –</span><span class="sxs-lookup"><span data-stu-id="0a0f4-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="0a0f4-168">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a0f4-168">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="0a0f4-169">Rozhraní ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="0a0f4-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0a0f4-170">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0a0f4-170">Related Sections</span></span>  
 [<span data-ttu-id="0a0f4-171">Výčty úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="0a0f4-171">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="0a0f4-172">Struktury úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="0a0f4-172">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="0a0f4-173">Ladění</span><span class="sxs-lookup"><span data-stu-id="0a0f4-173">Debugging</span></span>](../debugging/index.md)
