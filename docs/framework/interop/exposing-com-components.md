---
title: Vystavení komponent COM pro rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
ms.openlocfilehash: 914f72b5e4840555541943620ca2df1f629b0604
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123529"
---
# <a name="exposing-com-components-to-the-net-framework"></a>Vystavení komponent COM pro rozhraní .NET Framework
Tato část shrnuje proces potřebný k vystavení existující součásti modelu COM pro spravovaný kód. Podrobnosti o vytváření serverů COM, které úzce integrují s .NET Framework, najdete v tématu věnovaném [hlediskům návrhu pro spoluprovozování](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).
  
 Existující komponenty modelu COM jsou cenné prostředky ve spravovaném kódu jako obchodní aplikace střední vrstvy nebo jako izolované funkce. Ideální komponenta má primární spolupracující sestavení a je v souladu s požadavky na programování, které jsou uloženy v modelu COM.  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a>Vystavení komponent modelu COM pro .NET Framework  
  
1. [Importujte knihovnu typů jako sestavení](importing-a-type-library-as-an-assembly.md).  
  
     Modul CLR (Common Language Runtime) vyžaduje metadata pro všechny typy, včetně typů COM. Existuje několik způsobů, jak získat sestavení obsahující typy COM importované jako metadata.  
  
2. [Použijte typy com ve spravovaném kódu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).  
  
     Můžete zkontrolovat typy modelu COM, aktivovat instance a vyvolat metody objektu COM stejným způsobem jako u libovolného spravovaného typu.  
  
3. [Zkompilujte projekt interoperability](compiling-an-interop-project.md).  
  
     Windows SDK poskytuje kompilátory pro několik jazyků kompatibilních se specifikací CLS (Common Language Specification), včetně Visual Basic, C# a C++.  
  
4. [Nasazení aplikace spolupráce](deploying-an-interop-application.md)  
  
     Aplikace Interop jsou nejlépe nasazeny jako podepsaná sestavení v globální mezipaměti sestavení ( [silně pojmenovaná](../../standard/assembly/strong-named.md)).  
  
## <a name="see-also"></a>Viz také

- [Spolupráce s nespravovaným kódem](index.md)
- [Faktory návrhu pro spoluprovozování](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))
- [Ukázka zprostředkovatele s objekty COM: klient .NET a server COM](com-interop-sample-net-client-and-com-server.md)
- [Jazyková nezávislost a jazykově nezávislé komponenty](../../standard/language-independence-and-language-independent-components.md)
- [Gacutil. exe (nástroj Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md)
