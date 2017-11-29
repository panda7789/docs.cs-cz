---
title: "Kvalifikace typů .NET pro spolupráci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b6487c151f49f6084977deb600e7f93e5eb7acee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="qualifying-net-types-for-interoperation"></a>Kvalifikace typů .NET pro spolupráci
Pokud máte v úmyslu vystavit typy v sestavení aplikace modelu COM, zvažte požadavky na zprostředkovatel komunikace s objekty COM v době návrhu. Spravované typy (třída, rozhraní, struktura a výčet) se hladce integrují s typy modelu COM, když budete dodržovat následující pokyny:  
  
-   Třídy musí implementovat rozhraní explicitně.  
  
     I když se zprostředkovatel komunikace s objekty COM poskytuje mechanismus pro automatické generování rozhraní obsahující všechny členy třídy a členy základní třídy, je mnohem lepší zajistit explicitní rozhraní. Automaticky generovaného rozhraní nazývá rozhraní třídy. Pokyny najdete v části [představení rozhraní třídy](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024).  
  
     Můžete použít [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# a C++ začlenit definice rozhraní v kódu, místo nutnosti použít definice jazyka IDL (Interface) nebo jeho ekvivalent. Syntaxe podrobnosti najdete v dokumentaci jazyk.  
  
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
 [Vystavení součástí .NET Framework do modelu COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Představení rozhraní – třída](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)  
 [Použití atributů spolupráce](../../../docs/framework/interop/applying-interop-attributes.md)  
 [Balení sestavení pro model COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
