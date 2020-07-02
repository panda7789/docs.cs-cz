---
title: 'Postupy: Odkazování na typy .NET z modelu COM'
description: Odkazování na typy .NET z modelu COM. Klienti VB můžou zobrazit objekt .NET v prohlížeči objektů, ale klienti C++ musí odkazovat na soubor TLB s \# direktivou import.
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- importing type library
- COM interop, referencing .NET types
- interoperation with unmanaged code, referencing .NET types
- referencing .NET types
- interoperation with unmanaged code, importing type library
- type libraries
- COM interop, importing type library
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
ms.openlocfilehash: f8d052c7b9bac9c4bab61ab1950e9e89a7c73912
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618958"
---
# <a name="how-to-reference-net-types-from-com"></a>Postupy: Odkazování na typy .NET z modelu COM
Z hlediska kódu klienta a serveru jsou rozdíly mezi modelem COM a rozhraním .NET Framework z velké části nepostřehnutelné. Klienti aplikace Microsoft Visual Basic mohou zobrazovat objekt rozhraní .NET v prohlížeči objektů, který vystavuje metody objektu a syntaxi, vlastnosti a pole přesně tak, jako by se jednalo o jakýkoli jiný objekt modelu COM.  
  
 Proces importování knihovny typů je v případě klientů jazyka C++ poněkud složitější, ačkoli se pro exportování metadat do knihovny typů COM používají stejné nástroje. Chcete-li odkazovat na členy objektu .NET z nespravovaného klienta jazyka C++, odkazujte na soubor TLB (vytvořený pomocí Tlbexp.exe) s direktivou **#import** . Při odkazování na knihovnu typů z jazyka C++, je nutné buď zadat možnost **raw_interfaces_only** , nebo importovat definice v knihovně základní třídy mscorlib. tlb.  
  
### <a name="to-import-a-library"></a>Postup importování knihovny  
  
- Zadejte možnost **raw_interfaces_only** v direktivě **#import** . Příklad:  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     -nebo-  
  
- Zadejte také direktivu #import pro knihovnu Mscorlib.tlb. Příklad:  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Vystavení komponent architektury .NET Framework pro COM](exposing-dotnet-components-to-com.md)
- [Registrování sestav pomocí modelu COM](registering-assemblies-with-com.md)
- [Volání objektu .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))
- [Nasazení aplikace pro přístup k modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))
