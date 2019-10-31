---
title: ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
ms.openlocfilehash: db065357e22ac576600a3ca61dda0882b9206a86
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129152"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a>ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní
Umožňuje definovat nepovinné informace o asynchronních metodách pro každý symbol metody. Vždy používat s otevřenou metodou; To znamená, že mezi voláními [metody OpenMethod –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) a [metodou CloseMethod –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a>Metody  
 Toto rozhraní obsahuje následující metody:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DefineAsyncStepInfo – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|Definujte skupinu asynchronních operací await v aktuální metodě.<br /><br /> Každý posun výtěžnosti odpovídá instrukci vracené zpět, která identifikuje potenciální výtěžnost. Každý `breakpointMethod`/`breakpointOffset` páry identifikuje, kde bude asynchronní operace pokračovat; může se jednat o jinou metodu.|  
|[DefineCatchHandlerILOffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|Nastaví posun IL pro obslužnou rutinu catch generovaný kompilátorem, který zabalí asynchronní metodu.<br /><br /> Posunutí IL vygenerovaného catch je používáno ladicím programem pro zpracování tohoto zachycení, jako by šlo o neuživatelský kód, i když k tomu může dojít v metodě uživatelského kódu. Konkrétně se používá v reakci na událost **CatchHandlerFound** výjimky.|  
|[DefineKickoffMethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|Nastaví počáteční metodu, která inicializuje asynchronní operaci.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
