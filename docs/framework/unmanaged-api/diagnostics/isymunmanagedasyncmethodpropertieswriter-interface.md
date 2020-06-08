---
title: ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
ms.openlocfilehash: 04876483fd42e3f6e55222416fd0747891734a52
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501856"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a>ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní
Umožňuje definovat nepovinné informace o asynchronních metodách pro každý symbol metody. Vždy používat s otevřenou metodou; To znamená, že mezi voláními [metody OpenMethod –](isymunmanagedwriter-openmethod-method.md) a [metodou CloseMethod –](isymunmanagedwriter-closemethod-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a>Metody  
 Toto rozhraní obsahuje následující metody:  
  
|Metoda|Description|  
|------------|-----------------|  
|[DefineAsyncStepInfo – metoda](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|Definujte skupinu asynchronních operací await v aktuální metodě.<br /><br /> Každý posun výtěžnosti odpovídá instrukci vracené zpět, která identifikuje potenciální výtěžnost. Každý `breakpointMethod` / `breakpointOffset` pár identifikuje, kde se asynchronní operace obnoví; může to být jiná metoda.|  
|[DefineCatchHandlerILOffset – metoda](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|Nastaví posun IL pro obslužnou rutinu catch generovaný kompilátorem, který zabalí asynchronní metodu.<br /><br /> Posunutí IL vygenerovaného catch je používáno ladicím programem pro zpracování tohoto zachycení, jako by šlo o neuživatelský kód, i když k tomu může dojít v metodě uživatelského kódu. Konkrétně se používá v reakci na událost **CatchHandlerFound** výjimky.|  
|[DefineKickoffMethod – metoda](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|Nastaví počáteční metodu, která inicializuje asynchronní operaci.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní úložiště symbolů diagnostiky](diagnostics-symbol-store-interfaces.md)
