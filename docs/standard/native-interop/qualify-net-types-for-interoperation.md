---
title: Kvalifikace typů .NET pro mezichodové operace COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
ms.openlocfilehash: f0b9bc03225ae3d2365a21fd3b78d09c08d4fc1a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091582"
---
# <a name="qualifying-net-types-for-com-interoperation"></a>Kvalifikace typů .NET pro mezichodové operace COM
Pokud máte v úmyslu vystavovat typy v sestavení s aplikacemi modelu COM, zvažte požadavky zprostředkovatele komunikace s objekty COM v době návrhu. Spravované typy (třída, rozhraní, struktura a výčet) hladce integrují s typy modelu COM, když dodržujete následující pokyny:  
  
- Třídy by měly implementovat rozhraní explicitně.  
  
     I když zprostředkovatel komunikace s objekty COM poskytuje mechanismus pro automatické generování rozhraní obsahujícího všechny členy třídy a členy své základní třídy, je mnohem lepší poskytnout explicitní rozhraní. Automaticky generované rozhraní se nazývá rozhraní třídy. Pokyny naleznete v tématu [Představujeme rozhraní třídy](com-callable-wrapper.md#introducing-the-class-interface).  
  
     Můžete použít Visual Basic, C#a C++ k začleňování definic rozhraní do kódu, místo aby bylo nutné používat rozhraní IDL (Interface Definition Language) nebo jeho ekvivalent. Podrobnosti o syntaxi najdete v dokumentaci jazyka.  
  
- Spravované typy musí být veřejné.  
  
     Pouze veřejné typy v sestavení jsou registrovány a exportovány do knihovny typů. V důsledku toho jsou pro model COM viditelné pouze veřejné typy.  
  
     Spravované typy zpřístupňují funkce jinému spravovanému kódu, který nemusí být vystavený modelu COM. Například parametrizované konstruktory, statické metody a konstantní pole nejsou vystaveny klientům modelu COM. V případě, že modul runtime zařazování dat do a z typu, mohou být data zkopírována nebo transformována.  
  
- Metody, vlastnosti, pole a události musí být veřejné.  
  
     Členové veřejných typů musí být také veřejné, pokud mají být viditelné modelu COM. Můžete omezit viditelnost sestavení, veřejného typu nebo veřejných členů veřejného typu použitím <xref:System.Runtime.InteropServices.ComVisibleAttribute>. Ve výchozím nastavení jsou všechny veřejné typy a členy viditelné.  
  
- Typy musí mít veřejný konstruktor bez parametrů, který se má aktivovat z modelu COM.  
  
     Spravované, veřejné typy jsou viditelné v modelu COM. Nicméně bez veřejného konstruktoru bez parametrů (konstruktor bez argumentů) nemohou klienti modelu COM vytvořit typ. Klienti modelu COM mohou i nadále používat typ, pokud je aktivován jiným způsobem.  
  
- Typy nemohou být abstraktní.  
  
     Klienti modelu COM ani klienti rozhraní .NET nemohou vytvářet abstraktní typy.  
  
 Při exportu do modelu COM je Hierarchie dědičnosti spravovaného typu sloučena. Správa verzí se také liší mezi spravovanými a nespravovanými prostředími. Typy vystavené objektu COM nemají stejné charakteristiky verze jako jiné spravované typy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [Vystavení komponent architektury .NET Framework pro COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [Představení rozhraní třídy](com-callable-wrapper.md#introducing-the-class-interface)
- [Použití atributů spolupráce](../../../docs/standard/native-interop/apply-interop-attributes.md)
- [Balení .NET Framework sestavení pro model COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
