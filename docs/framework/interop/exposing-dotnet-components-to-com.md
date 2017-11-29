---
title: "Vystavení komponent architektury .NET Framework pro COM"
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
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9451504b64ddaa8dc0ea6b3a0754257b2c8b3824
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="exposing-net-framework-components-to-com"></a>Vystavení komponent architektury .NET Framework pro COM
Zápis typ formátu .NET a využívání tohoto typu z nespravovaného kódu jsou odlišné aktivity pro vývojáře. Tato část popisuje několik tipy pro vytvoření spravovaného kódu, které spolupracuje s klienty COM:  
  
-   [Kvalifikace typů .NET pro spolupráci](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).  
  
     Všechny spravované typy, metody, vlastnosti, pole a události, které chcete vystavit do modelu COM musí být veřejné. Typy musí mít veřejný výchozí konstruktor, který je jediný konstruktor, který lze vyvolat prostřednictvím modelu COM.  
  
-   [Použití atributů spolupráce](../../../docs/framework/interop/applying-interop-attributes.md).  
  
     Vlastní atributy v rámci spravovaného kódu můžete zlepšení interakce komponenty.  
  
-   [Balení sestavení pro model COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).  
  
     Vývojáři COM může vyžadovat, je vytvořit shrnutí jednotlivými kroky při odkazování na a nasazení vaší sestavení.  
  
 Kromě toho tato část popisuje úlohy související s využívání spravovaný typ z modelu COM klienta.  
  
#### <a name="to-consume-a-managed-type-from-com"></a>Chcete-li využívat spravovaný typ z modelu COM  
  
1.  [Zaregistrovat sestavení modelu COM](../../../docs/framework/interop/registering-assemblies-with-com.md).  
  
     Typy v sestavení (a knihovny typů) musí být zaregistrován v době návrhu. Pokud instalační program nezaregistruje sestavení, požádejte COM vývojářům používat Regasm.exe.  
  
2.  [Referenční typy .NET z modelu COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).  
  
     Vývojáři COM můžete odkazovat typy v sestavení pomocí stejné nástroje a techniky, které používají ještě dnes.  
  
3.  [Volání objektu .NET](http://msdn.microsoft.com/en-us/40c9626c-aea6-4bad-b8f0-c1de462efd33).  
  
     Vývojáři COM můžete volat metody pro objekt .NET stejným způsobem jako volání metody v libovolném nespravované typu. Například COM **CoCreateInstance** aktivuje objekty .NET API.  
  
4.  [Nasazení aplikace pro přístup COM](http://msdn.microsoft.com/en-us/fb63564c-c1b9-4655-a094-a235625882ce).  
  
     Sestavení se silným názvem může být nainstalována v globální mezipaměti sestavení a vyžaduje podpis vydavatele. Sestavení, které nejsou silné s názvem musí být nainstalován v adresáři aplikace klienta.  
  
## <a name="see-also"></a>Viz také  
 [Spolupráce s nespravovaným kódem](../../../docs/framework/interop/index.md)  
 [Ukázka zprostředkovatele komunikace s objekty COM: Klient COM a .NET serveru](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
