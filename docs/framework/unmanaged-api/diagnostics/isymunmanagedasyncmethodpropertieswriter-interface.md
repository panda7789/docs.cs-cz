---
title: "ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99d61fdb9f7e3eb2bc10de7584061d8922bf9285
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a>ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní
Umožňuje zadat informace volitelné asynchronní metoda pro každou metodu symbol. Vždy používat s otevřenou metoda; To znamená mezi volání [openmethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) a [closemethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a>Metody  
 Toto rozhraní obsahuje následující metody:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DefineAsyncStepInfo – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|Definujte skupinu asynchronních operací v aktuální metoda await.<br /><br /> Každý yield posun odpovídá návratový instrukce await, identifikace potenciální upozornění. Každý `breakpointMethod` / `breakpointOffset` pár identifikuje, kde bude pokračovat asynchronní operaci; může být v jinou metodu.|  
|[DefineCatchHandlerILOffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|Nastaví IL posunutí pro generované kompilátorem catch obslužná rutina, která zabalí asynchronní metody.<br /><br /> Posun IL generovaného catch je používán ladicího programu pro zpracování catch, jako by šlo bez uživatelského kódu, i když může dojít v metodu kódu uživatele. Konkrétně se používá v reakci **CatchHandlerFound** události výjimky.|  
|[DefineKickoffMethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|Nastaví počáteční metody, která zahájí asynchronní operace.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
