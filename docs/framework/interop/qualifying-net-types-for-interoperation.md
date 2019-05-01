---
title: Kvalifikace typů .NET pro spolupráci
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cad67f52a4ca977606d7b5a307868ff129570e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032653"
---
# <a name="qualifying-net-types-for-interoperation"></a>Kvalifikace typů .NET pro spolupráci
Pokud chcete vystavit typy v sestavení aplikace modelu COM, zvažte požadavky na spolupráci s COM v době návrhu. Spravované typy (třída, rozhraní, struktury a výčet) bez problémů integrovat typy modelu COM při dodržovat následující pokyny:  
  
- Třídy musí implementovat rozhraní explicitně.  
  
     Ačkoli komunikace s objekty COM poskytuje mechanismus pro automatické generování rozhraní obsahující všechny členy třídy a členy své základní třídy, je mnohem lepší poskytnout explicitní rozhraní. Automaticky generovaného rozhraní je volat rozhraní třídy. Pokyny najdete v části [představení rozhraní třídy](com-callable-wrapper.md#introducing-the-class-interface).  
  
     Můžete použít v jazyce Visual Basic C#a C++ až po začlenění definice rozhraní ve vašem kódu, místo nutnosti použít rozhraní Definition Language (IDL) nebo jeho ekvivalent. Podrobnosti o syntaxi naleznete v dokumentaci jazyka.  
  
- Spravované typy musí být veřejné.  
  
     Pouze veřejné typy v sestavení jsou registrovány a exportovat do knihovny typů. V důsledku toho pouze veřejné typy jsou viditelné v modelu COM.  
  
     Spravované typy zveřejňují funkce pro další spravovaný kód, který nemusí být vystaveny objektům modelu COM. Například konstruktor s parametry, statické metody a konstantní pole nejsou zveřejněné klientům modelu COM. Dále jak modul runtime zařazuje dat do a z typu, data může kopírovat nebo transformovat.  
  
- Metody, vlastnosti, pole a události musí být veřejné.  
  
     Členové veřejné typy musí být také veřejné, pokud mají být viditelné modelu COM. Můžete omezit, zda se sestavení, veřejný typ nebo veřejné členy typu public použitím <xref:System.Runtime.InteropServices.ComVisibleAttribute>. Ve výchozím nastavení jsou viditelné všechny veřejné typy a členy.  
  
- Typy musí mít veřejný výchozí konstruktor, chcete-li aktivovat z modelu COM.  
  
     Spravovaná, veřejné typy jsou viditelné v modelu COM. Ale bez veřejného výchozího konstruktoru (konstruktor bez argumentů), nelze vytvořit klientům modelu COM typu. Klientům modelu COM můžete stále použít typ, pokud je aktivovaná jiným způsobem.  
  
- Typy nemohou být abstraktní.  
  
     Klienti modelu COM ani klientů .NET můžete vytvořit abstraktní typy.  
  
 Při exportu do modelu COM, hierarchie dědičnosti spravovaného typu se sloučí. Správa verzí se také liší mezi spravovanými a nespravovanými prostředí. Typy vystavit rozhraní COM nemají stejné vlastnosti jako jiné spravované typy správy verzí.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [Vystavení komponent architektury .NET Framework pro COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [Představení rozhraní třídy](com-callable-wrapper.md#introducing-the-class-interface)
- [Použití atributů spolupráce](../../../docs/framework/interop/applying-interop-attributes.md)
- [Zabalení sestavení pro model COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
