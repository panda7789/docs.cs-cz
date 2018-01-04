---
title: "Vystavení komponent COM pro rozhraní .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9361de4726b1dc58238db5ca7b5605f2cc75485d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="exposing-com-components-to-the-net-framework"></a>Vystavení komponent COM pro rozhraní .NET Framework
Tento oddíl shrnuje proces nutný k zpřístupnění existující součást COM do spravovaného kódu. Podrobnosti o zápis servery COM, která úzce integrovat s rozhraním .NET Framework, najdete v části [aspekty návrhu pro spolupráci](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689).  
  
 Existující součásti COM jsou cenné prostředky ve spravovaném kódu jako střední vrstvu obchodní aplikace nebo jako izolované funkce. Ideální součást má primární spolupracující sestavení a úzce vyhovuje standardům programovací způsobené COM.  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a>K vystavení součástí COM v rozhraní .NET Framework  
  
1.  [Import knihovny typů jako sestavení](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md).  
  
     Modul common language runtime požaduje metadata pro všechny typy, včetně typy modelu COM. Existuje několik způsobů, jak získat sestavení obsahující typy modelu COM importován jako metadata.  
  
2.  [Vytvoření typů COM ve spravovaném kódu](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66).  
  
     Můžete zkontrolovat typy modelu COM, aktivovat instancí a vyvolání metody pro objekt COM stejným způsobem jako u jakékoli spravovaného typu.  
  
3.  [Kompilace projektu interoperability](../../../docs/framework/interop/compiling-an-interop-project.md).  
  
     [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Poskytuje kompilátory pro několik jazyků kompatibilní s specifikace CLS (Common Language), včetně [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# a C++.  
  
4.  [Nasazení aplikace spolupráce](../../../docs/framework/interop/deploying-an-interop-application.md).  
  
     Spolupráce – aplikace nejlépe nasazených jako [silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md), podepsané sestavení v globální mezipaměti sestavení.  
  
## <a name="see-also"></a>Viz také  
 [Spolupráce s nespravovaným kódem](../../../docs/framework/interop/index.md)  
 [Aspekty návrhu pro spolupráci](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)  
 [Ukázka zprostředkovatele s objekty COM: klient .NET a server COM](../../../docs/framework/interop/com-interop-sample-net-client-and-com-server.md)  
 [Jazyková nezávislost a jazykově nezávislé komponenty](../../../docs/standard/language-independence-and-language-independent-components.md)  
 [Gacutil.exe (nástroj globální mezipaměti sestavení)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
