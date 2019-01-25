---
title: Vystavení komponent COM pro rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff12472ae5c7b2abbf1af338c2a1aea2a72907d6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677144"
---
# <a name="exposing-com-components-to-the-net-framework"></a>Vystavení komponent COM pro rozhraní .NET Framework
Tento oddíl shrnuje procesu nutné vystavit existující komponenty modelu COM pro spravovaný kód. Podrobnosti o vytváření serverů modelu COM, který úzce integrace s rozhraním .NET Framework, naleznete v tématu [aspekty návrhu pro spolupráci](https://msdn.microsoft.com/library/b59637f6-fe35-40d6-ae72-901e7a707689(v=vs.100)).
  
 Střední vrstvy obchodní aplikace nebo jako izolované funkce stávající komponentami modelu COM jsou cenné prostředky ve spravovaném kódu. Ideální komponenta má primární sestavení zprostředkovatele komunikace a úzce odpovídá programovacím standardy stanovené modelu COM.  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a>Vystavení komponent COM pro rozhraní .NET Framework  
  
1.  [Import knihovny typů jako sestavení,](importing-a-type-library-as-an-assembly.md).  
  
     Modul common language runtime požaduje metadata pro všechny typy, včetně typů modelu COM. Existuje několik způsobů, jak získat sestavení obsahující typy modelu COM importovat jako metadata.  
  
2.  [Vytvoření typů modelu COM ve spravovaném kódu](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100)).  
  
     Můžete kontrolovat typy modelu COM, aktivovat instance a volat metody u objektu COM stejným způsobem jako u jakékoli spravovaného typu.  
  
3.  [Kompilace projektu interoperability](compiling-an-interop-project.md).  
  
     [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Obsahuje kompilátory pro několik jazyků kompatibilních s specifikace CLS (Common Language), včetně [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#a C++.  
  
4.  [Nasazení aplikace spolupráce](deploying-an-interop-application.md).  
  
     Spolupráce – aplikace se nejlépe nasadit jako [silným názvem](../app-domains/strong-named-assemblies.md), podepsaná sestavení v globální mezipaměti sestavení.  
  
## <a name="see-also"></a>Viz také:
- [Spolupráce s nespravovaným kódem](index.md)
- [Aspekty návrhu pro spolupráci](https://msdn.microsoft.com/library/b59637f6-fe35-40d6-ae72-901e7a707689(v=vs.100))
- [Ukázka zprostředkovatele s objekty COM: klient .NET a server COM](com-interop-sample-net-client-and-com-server.md)
- [Jazyková nezávislost a jazykově nezávislé komponenty](../../standard/language-independence-and-language-independent-components.md)
- [Gacutil.exe (nástroj globální mezipaměti sestavení)](../tools/gacutil-exe-gac-tool.md)
