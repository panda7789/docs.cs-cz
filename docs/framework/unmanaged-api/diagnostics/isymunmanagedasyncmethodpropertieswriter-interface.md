---
title: ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82fcddd7a3f89a92cc79285930b30342333fbec2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59112395"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a>ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní
Můžete zadat volitelný asynchronní informace metody pro každou metodu symbol. Vždy používejte otevřené metodou; To znamená, že mezi voláními [openmethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) a [closemethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a>Metody  
 Toto rozhraní obsahuje následující dvě metody:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DefineAsyncStepInfo – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|Definujte skupinu asynchronního await operací v aktuální metodě.<br /><br /> Každý yield posun odpovídá návratový instrukce await, identifikace možných yield. Každý `breakpointMethod` / `breakpointOffset` pár identifikuje, kde asynchronní operace bude pokračovat, může být v jiné metody.|  
|[DefineCatchHandlerILOffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|Nastavuje posun pro obslužnou rutinu catch vygenerovaný kompilátorem, který obtéká asynchronní metody IL.<br /><br /> Posun IL generovaný catch používá ladicí program na zpracování bloku catch, jako by šlo neuživatelský kód, i v případě, že může dojít v metodě kód uživatele. Zejména je použít v odpovědi **CatchHandlerFound** události výjimky.|  
|[DefineKickoffMethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|Nastaví výchozí metodu, která zahájí asynchronní operace.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
