---
title: 'Postupy: Odkazování na typy .NET z modelu COM'
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
ms.openlocfilehash: 0223cb25b933cc84af49aa86d90259fdf1fd3efc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124175"
---
# <a name="how-to-reference-net-types-from-com"></a>Postupy: Odkazování na typy .NET z modelu COM
Z hlediska kódu klienta a serveru jsou rozdíly mezi modelem COM a rozhraním .NET Framework z velké části nepostřehnutelné. Klienti aplikace Microsoft Visual Basic mohou zobrazovat objekt rozhraní .NET v prohlížeči objektů, který vystavuje metody objektu a syntaxi, vlastnosti a pole přesně tak, jako by se jednalo o jakýkoli jiný objekt modelu COM.  
  
 Proces importování knihovny typů je v případě klientů jazyka C++ poněkud složitější, ačkoli se pro exportování metadat do knihovny typů COM používají stejné nástroje. Chcete-li odkazovat na členy objektu .NET z nespravovaného klienta jazyka C++, odkazujte na soubor TLB (vytvořený pomocí Tlbexp. exe) pomocí direktivy **#import** . Při odkazování na knihovnu typů z jazyka C++, je nutné buď zadat možnost **raw_interfaces_only** , nebo importovat definice v knihovně základní třídy mscorlib. tlb.  
  
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
  
## <a name="see-also"></a>Viz také

- [Vystavení komponent architektury .NET Framework pro COM](exposing-dotnet-components-to-com.md)
- [Registrování sestav pomocí modelu COM](registering-assemblies-with-com.md)
- [Volání objektu .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))
- [Nasazení aplikace pro přístup k modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))
