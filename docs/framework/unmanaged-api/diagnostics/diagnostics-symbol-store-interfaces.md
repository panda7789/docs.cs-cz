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
# <a name="diagnostics-symbol-store-interfaces"></a>Rozhraní úložiště symbolů diagnostiky
This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [IBindingDisplay – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 Provides methods that display current binding information about the running application.  
  
 [IDebugAutoAttach – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 Defines the interface for a server-invoked debugger auto attach.  
  
 [INotifyConnection2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 Declares methods for registering and unregistering a connection notification source.  
  
 [INotifySink2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 Declares methods for sink notification.  
  
 [INotifySource2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 Declares a method for setting notification filters.  
  
 [ISymENCUnmanagedMethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 Provides information for the Edit and Continue feature.  
  
 [ISymUnmanagedAsyncMethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).  
  
 [ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 Allows definition of optional async method information per method symbol. Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).  
  
 [ISymUnmanagedBinder – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 Represents a symbol binder for unmanaged code.  
  
 [ISymUnmanagedBinder2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.  
  
 [ISymUnmanagedBinder3 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.  
  
 [ISymUnmanagedConstant – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 Provides access to unmanaged constants.  
  
 [ISymUnmanagedDispose – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 Disposes of unmanaged resources.  
  
 [ISymUnmanagedDocument – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 Represents a document referenced by a symbol store.  
  
 [ISymUnmanagedDocumentWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 Provides methods for writing to a document referenced by a symbol store.  
  
 [ISymUnmanagedENCUpdate – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 Provides methods for the Edit and Continue feature.  
  
 [ISymUnmanagedMethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 Represents a method within the symbol store.  
  
 [ISymUnmanagedNamespace – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 Represents a namespace.  
  
 [ISymUnmanagedReader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.  
  
 [ISymUnmanagedReader2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 Gets a symbol reader method given a method token and an edit-and-copy version number.  
  
 [ISymUnmanagedReaderSymbolSearchInfo – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 Provides methods that get symbol search information.  
  
 [ISymUnmanagedScope – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 Represents a lexical scope within a method.  
  
 [ISymUnmanagedScope2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..  
  
 [ISymUnmanagedSourceServerModule – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 Provides source server data for a module.  
  
 [ISymUnmanagedSymbolSearchInfo – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 Provides methods that get information about the search path.  
  
 [ISymUnmanagedVariable – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 Represents a variable, such as a parameter, a local variable, or a field.  
  
 [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.  
  
 [ISymUnmanagedWriter2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables. Extends the `ISymUnmanagedWriter` interface.  
  
 [ISymUnmanagedWriter3 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables. Extends the `ISymUnmanagedWriter` interface.  
  
 [ISymUnmanagedWriter4 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 ISymUnmanagedWriter4 interface.  
  
 [ISymUnmanagedWriter5 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 ISymUnmanagedWriter5 interface.  
  
## <a name="related-sections"></a>Související oddíly  
 [Výčty pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [Struktury pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
