---
title: "Kvalifikace typů .NET pro spolupráci"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
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
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b0a6d6a2a8139127b46484f972eb797642b4ee53
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="qualifying-net-types-for-interoperation"></a>Kvalifikace typů .NET pro spolupráci
Pokud máte v úmyslu vystavit typy v sestavení aplikace modelu COM, zvažte požadavky na zprostředkovatel komunikace s objekty COM v době návrhu. Spravované typy (třída, rozhraní, struktura a výčet) se hladce integrují s typy modelu COM, když budete dodržovat následující pokyny:  
  
-   Třídy musí implementovat rozhraní explicitně.  
  
     I když se zprostředkovatel komunikace s objekty COM poskytuje mechanismus pro automatické generování rozhraní obsahující všechny členy třídy a členy základní třídy, je mnohem lepší zajistit explicitní rozhraní. Automaticky generovaného rozhraní nazývá rozhraní třídy. Pokyny najdete v části [představení rozhraní třídy](com-callable-wrapper.md#introducing-the-class-interface).  
  
     Visual Basic, C# a C++ slouží k začlenit definice rozhraní v kódu, místo nutnosti použít definice jazyka IDL (Interface) nebo jeho ekvivalent. Syntaxe podrobnosti najdete v dokumentaci jazyk.  
  
-   Spravované typy musí být veřejné.  
  
     Pouze veřejné typy v sestavení jsou zaregistrované a exportují do knihovny typů. V důsledku toho jsou pouze veřejné typy viditelné modelu COM.  
  
     Spravované typy zveřejněte funkce do jiných spravovaného kódu, která nemusí být vystavena modelu COM. Parametrizované konstruktory, statické metody a konstantní pole nejsou pro instanci zveřejněné klientům COM. Navíc jako modul runtime zařazuje dat a deaktivovat typu, data mohou kopírovat nebo transformovat.  
  
-   Metody, vlastnosti, pole a události musí být veřejné.  
  
     Členové veřejné typy musí být také veřejné, pokud mají být viditelné modelu COM. Můžete omezit viditelnost sestavení, typu veřejný nebo veřejné členy veřejného typu použitím <xref:System.Runtime.InteropServices.ComVisibleAttribute>. Ve výchozím nastavení jsou zobrazené všechny veřejné typy a členy.  
  
-   Typy musí mít veřejný výchozí konstruktor chcete aktivovat. z modelu COM.  
  
     Spravované, veřejné typy jsou viditelné pro COM. Bez výchozí veřejný konstruktor (konstruktor bez argumentů), ale klienti COM nelze vytvořit typ. Klienti COM můžete dál používat typ, pokud je aktivovaná jiným způsobem.  
  
-   Typy nemohou být abstraktní.  
  
     Klienti COM ani klientů .NET můžete vytvořit abstraktní typy.  
  
 Při exportu do modelu COM, se sloučí hierarchie dědičnosti spravovaného typu. Správa verzí se také liší mezi spravovanými a nespravovanými prostředí. Typy vystaven objektům modelu COM nemají stejné vlastnosti Správa verzí jako jiné spravované typy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>  
 [Vystavení komponent architektury .NET Framework pro COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Představení rozhraní – třída](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)  
 [Použití atributů spolupráce](../../../docs/framework/interop/applying-interop-attributes.md)  
 [Zabalení sestavení pro model COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
